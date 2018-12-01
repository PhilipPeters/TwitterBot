// 'ENTER YOUR OWN CREDENTIALS' means you should create your own Twitter Developer Account to receive your own credentials

const args = process.argv;


if (args.length <= 2){
  hashtag = '#Spurs'
  console.log('bug');
  reply = "Spurs are the best :)"
}

else{

text = args.slice(3);

hashtag = args[2];




if (hashtag.charAt(0) != '#'){
  hashtag = "#".concat(hashtag);
console.log("hashtag set is " + hashtag);
}

if (args.length <= 3){

  reply = "Spurs are the best :)"
}
else{
text = args.splice(3);
reply = text.join(" ");
}
}
console.log("reply set is " + reply);

var TwitterPackage = require('twitter');

var secret = {
  
  consumer_key: 'ENTER YOUR OWN CREDENTIALS',
  consumer_secret: 'ENTER YOUR OWN CREDENTIALS',
  access_token_key: 'ENTER YOUR OWN CREDENTIALS',
  access_token_secret: 'ENTER YOUR OWN CREDENTIALS'

}
var Twitter = new TwitterPackage(secret);

// Call the stream function and pass in 'statuses/filter', our filter object, and our callback
Twitter.stream('statuses/filter', {track: hashtag}, function(stream) {

  // ... when we get tweet data...
  stream.on('data', function(tweet) {

    // print out the text of the tweet that came in
    console.log(tweet.text);

    //build our reply object
    var statusObj = {status: "Hi @" + tweet.user.screen_name + ", " + reply}

    //call the post function to tweet something
    Twitter.post('statuses/update', statusObj,  function(error, tweetReply, response){

      //if we get an error print it out
      if(error){
        console.log(error);
      }

      //print the text of the tweet we sent out
      console.log(tweetReply.text);
    });
  });

  // ... when we get an error...
  stream.on('error', function(error) {
    //print out the error
    console.log(error);
  });
});
