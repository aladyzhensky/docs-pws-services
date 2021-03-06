---
title: PubNub
---

PubNub enables software developers to rapidly build and scale real-time apps by providing the global infrastructure that connects key building blocks for real-time interactivity.

PubNub utilizes a Publish/Subscribe model for real-time data streaming and device signaling. PubNub supports: WebSockets, Socket.IO, SignalIR, WebRTC Data Channel and other streaming protocols.

## <a id='managing'></a>Managing Services ##

PubNub doesn't currently support binding. To publish and subscribe to PubNub you would need to add PubNub to your space by selecting the appropriate plan from the Marketplace.

After selecting the plan, you can obtain your publish and subscribe keys by going to your space's **Services** section and selecting **Manage** of the PubNub service.

## <a id='using'></a>Using PubNub Within Your Application ##
Once you obtain the Subscription and Publish keys you can use one of the many available SDKs in your application to publish and subscribe to messages from PubNub

SDK and further help is available here: https://www.pubnub.com/developers/

## <a id='sample-applications'></a>Sample Applications ##

Publishing a message to PubNub in Java:

 ~~~
 Pubnub pubnub = new Pubnub("demo", "demo");
 try {
   pubnub.subscribe("hello_world", new Callback() {
        @Override
       public void connectCallback(String channel, Object message) {
           System.out.println("SUBSCRIBE : CONNECT on channel:" + channel
                      + " : " + message.getClass() + " : "
                      + message.toString());
       }

       @Override
       public void disconnectCallback(String channel, Object message) {
           System.out.println("SUBSCRIBE : DISCONNECT on channel:" + channel
                      + " : " + message.getClass() + " : "
                      + message.toString());
       }

       public void reconnectCallback(String channel, Object message) {
           System.out.println("SUBSCRIBE : RECONNECT on channel:" + channel
                      + " : " + message.getClass() + " : "
                      + message.toString());
       }

       @Override
       public void successCallback(String channel, Object message) {
           System.out.println("SUBSCRIBE : " + channel + " : "
                      + message.getClass() + " : " + message.toString());
       }

       @Override
       public void errorCallback(String channel, PubnubError error) {
           System.out.println("SUBSCRIBE : ERROR on channel " + channel
                      + " : " + error.toString());
       }
     }
   );
 } catch (PubnubException e) {
   System.out.println(e.toString());
 }

 Callback callback = new Callback() {
   public void successCallback(String channel, Object response) {
     System.out.println(response.toString());
   }
   public void errorCallback(String channel, PubnubError error) {
   System.out.println(error.toString());
   }
 };
 pubnub.publish("demo", "Hello World !!" , callback);
~~~

## <a id='support'></a>Support ##
PubNub support resources: http://support.pubnub.com/

## <a id='reources'></a>Additional Resources ##
https://www.pubnub.com/docs/
