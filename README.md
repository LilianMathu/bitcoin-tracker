# bitcoin-tracker

<h3>Introduction to Bitcoin App</h3>
<p>In this project we will build an app to track the changes in bitcoin currency using the Bitcoin China API. We'll be using jQuery and Bootstrap within an HTML page to display the buy and sell prices of bitcoins in real-time. This application will help us to better understand the format of the data being sent to the view, and how to compose the streaming data into a readable table.
</p>

 <h3>Bitcoin App Scaffold</h3><br>
Let's begin this project by taking a look at the API we'll be using, which can be found here at btcc. com/apidocs. This site provides us with a number of different APIs to access. Let's click on the one that says WebSocket. This API is set up to work with Socket. io, so that all we need to do is require in Socket. io, and then set our socket to the btcc. com API URL. Then we're able to subscribe to any one of these markets. After subscribing we can then listen for a ticker, which will be giving us JSON objects in real-time that look similar to this example. Switching back over to Sublime Text, I've opened up a folder called btcApp, and this folder can be found as part of your resource's files, as well as here on GitHub. This folder contains the beginning code we'll need for this project. So let's open up the starter code and see what's inside. We'll start with an app. js file that has a basic Express server set up to use Socket. io. We're serving up a view from the public folder using the express. static method, and in our node_modules folder you can see that we've already added express, path, as well as socket. io. In our HTML file we've included a style reference to Bootstrap via cdn, then I've created a header area to display the market along with highs and lows, and then below that we'll display a Recent Trades, inside there we'll show both the buy and sell price, along with the trade volume. We'll be using jQuery to assist in displaying the data into our defined IDs, and then at the bottom here I've made sure to include socket. io's script. With that covered let's take a look at what our starting app looks like. We'll navigate into the location of my project in my terminal, and start the server by typing node, and then app. js. Navigating over to localhost:8080, we can see how our sample app will look before any data is added.

 <h3>Bitcoin App Build</h3> <br>
Let's now hook up to the Bitcoin API so that we can start streaming in some data. First, we'll open up our index. html file and scroll to the bottom. I'm going to include a script tag and set up a socket that connects to the Bitcoin China API. Next, I'm going to subscribe to one of their data points called marketdata_cnybtc. I need to create a connection to the socket, and this can be done using the on method. Then inside of the connection I can listen for a ticker event, and each time an event happens we'll be passed a JSON object, and the JSON object that we get back would be stored here in this data argument. We'll also include a log message here so that we can take a look at the object we're being passed inside of our browser console. I'll navigate now into my project location in the terminal and type the command node app. js. When we go to our localhost:8080 and open up the console, we can see objects start appearing. If we open one up, we can see it looks just like what we would expect as given to us within the API docs. Let's now add our jQuery using this data argument to populate the bitcoin data into our HTML. We'll start by adding the name of the market to the ID we created called market, (Working) and we define this up above in our code. Now, let's create the jQuery code to populate the high and low areas found here. I will use the ID of high-count, and the data. ticker. high value, and then I'll do the same for the low-count and add in data. ticker. low value. I'm going to copy over this format and just change the values around. First, for the buy price, and next for the sell price, and finally for the volume amount. And these will end up being displayed here and here. And now, with everything in place, let's restart our server and refresh our browser. You might have to wait a few seconds for the first object to come through, and once it does, we can see the buy and sell prices along with the volume being updated in real time.
