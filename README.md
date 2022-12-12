# Unity-MQTT-Setup

First Step - Publish a valuable you would like to subscribe from other agent through mqtt, for example:

        public float seconds = 0f;
        public float minutes = 0f;
        public bool cellPhone = false;
        public bool teddyBear = false;
        public bool wineGlass = false;
        

Second Step - In the SubscribeTopics, add your mqtt topic with the following format:

        protected override void SubscribeTopics()
        {
            client.Subscribe(new string[] { "jieThesis/Oculus/seconds" }, new byte[] { MqttMsgBase.QOS_LEVEL_EXACTLY_ONCE });
            client.Subscribe(new string[] { "jieThesis/Oculus/minutes" }, new byte[] { MqttMsgBase.QOS_LEVEL_EXACTLY_ONCE });
            client.Subscribe(new string[] { "jieThesis/Oculus/cellPhone" }, new byte[] { MqttMsgBase.QOS_LEVEL_EXACTLY_ONCE });
            client.Subscribe(new string[] { "jieThesis/Oculus/teddyBear" }, new byte[] { MqttMsgBase.QOS_LEVEL_EXACTLY_ONCE });
            client.Subscribe(new string[] { "jieThesis/Oculus/wineGlass" }, new byte[] { MqttMsgBase.QOS_LEVEL_EXACTLY_ONCE });

        }
        
 Third Step - In the DecodeMessage, add your topic related to the value in a if statement in the following format:
 
        protected override void DecodeMessage(string topic, byte[] message)
        {
            string msg = System.Text.Encoding.UTF8.GetString(message);
            
            StoreMessage(msg);
            

            if (topic == "jieThesis/Oculus/seconds")
            {
                
                seconds = Single.Parse(msg);
                
            }
            
 ## Cite
 https://github.com/gpvigano/M2MqttUnity
