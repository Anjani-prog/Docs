
 
  1. CameraRoll Picker component for React native(https://www.npmjs.com/package/react-native-camera-roll-picker)
             
             npm install react-native-camera-roll-picker --save
            
  2.A cross-platform (iOS / Android), fully customizable, React Native Navigation Bar component.(https://www.npmjs.com/package/react-native-nav)
            
            npm install  react-native-nav --save 
  
  3.React Native Map components for iOS + Android (https://www.npmjs.com/package/react-native-maps)
           
           npm install react-native-maps --save
 
 
(https://www.valentinog.com/blog/socket-io-node-js-react/)


### Making use of our realtime server: the React client

If it’s your first time with React, install create-react-app to get started quickly by running:

     react-native init socket-io-client
move inside the newly created directory:

     cd socket-io-client
and install the Socket.IO client:

     npm install socket.io-client
finally start the development React server:

     react-native start
     react-native run-ios
     react-native run-ios --simulator="iPhone X"
     react-native run-android

To keep things simple we will just use the App.js component which lies inside the src directory.

Open up App.js. You can safely remove all the content inside the file and replace the code with the following:

    import React, { Component } from "react";
    import socketIOClient from "socket.io-client";
    class App extends Component {
      constructor() {
        super();
        this.state = {
          response: false,
          endpoint: "http://127.0.0.1:4001"
        };
      }
      componentDidMount() {
        const { endpoint } = this.state;
        const socket = socketIOClient(endpoint);
        socket.on("FromAPI", data => this.setState({ response: data }));
      }
      render() {
        const { response } = this.state;
        return (
          <div style={{ textAlign: "center" }}>
            {response
              ? <p>
                  The temperature in Florence is: {response} °F
                </p>
              : <p>Loading...</p>}
          </div>
        );
      }
    }
    export default App;

now point your browser to http://localhost:3000 and wait 10 seconds. You should see the following output (I’ve added some styling to my component, feel free to add some CSS to your App.js too):

 Socket.IO and React paired together

If you keep an eye on the page you’ll notice the temperature changing over time, every 10 seconds.

It’s the magic of Socket.IO: as soon as the React component gets mounted, the componentDidMount creates a new connection to our Socket.IO server by instantiating a new socket:

    const socket = socketIOClient(endpoint);
    If you remember, the socket is a communication channel and we’re able to listen for any event happening inside it:

    socket.on("FromAPI", data => this.setState({ response: data }));
    If you take a look at the server-side code, the “FromAPI” message/event gets fired as soon as a new client connects to       the server.

The client can listen for the event with the on() method and do something with the data contained inside the message/event. In our case we simply want to store the temperature inside our component’ store.

That’s it! Once established, the connection will receive the updates from the server without any need to refresh the page!

