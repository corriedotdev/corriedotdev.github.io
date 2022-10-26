---
layout: post
title: Download - Spotify Playlist to CSV App & Sentence a Day App 
excerpt: "Two simple C# projects that I wanted to make for myself. One allows for a diary entry for each day using some old windows forms code that allows for minimizing to icon tray, progressive and can be continually worked on while functionality is still supported. The Spotify grabber returns all the songs in a play list with their artist and album, great if you want to migrate away from Spotify and move onto another platform without losing playlists, or just to keep regular back ups of your beloved playlists. "
categories: [Download🔻]
comments: true
---

# Spotify Grabber
Next is another simple application that is useful to keeping that inner demon I have about losing personal data. My personally curated playlists. We all have them, but we don't necessarily own them. I rely exclusively on Spotify for my playlists and when I have a song I like, it gets added to a playlist which suits the vibe.

Its not hard to accidentally delete a playlist, its two clicks and irreversible. Also should the platform fade off (which I doubt) I lose the songs and artists and songs. The application simply takes the OAUTH credentials from your account so you will need to visit the spotify developer page and get these credentials. Its free. Once you enter this into the terminal you enter the playlist ID and thats all there is to it. A CSV with the artists and songs will be exported to your desktop or designated location from the app.config.

![Grabber image]({{ site.url }}/img/grabber-1.PNG)
{: .pull-center}

## HTTP Auth
The main two functions that get this to work (excuse the json parsing not using a lib but quicker to stick with what you know to do in 5 mins for little personal applets.)
{% highlight csharp %}
public string GetTrackInfo(string url) {

            string webResponse = string.Empty;
            var myToken = GetAccessToken();

            try {
                // Get token for request
                HttpClient hc = new HttpClient();
                var request = new HttpRequestMessage() {
                    RequestUri = new Uri(url),
                    Method = HttpMethod.Get
                };

                request.Headers.Accept.Add(new MediaTypeWithQualityHeaderValue("application/json"));
                request.Headers.Authorization = new AuthenticationHeaderValue("Authorization", "Bearer " + myToken);

                var task = hc.SendAsync(request).ContinueWith((taskwithmsg) => {
                        var response = taskwithmsg.Result;
                        var jsonTask = response.Content.ReadAsStringAsync();
                        webResponse = jsonTask.Result;
                });

                task.Wait();


            } catch (WebException ex) {
                Console.WriteLine("Track Request Error: " + ex.Status);
            } catch (TaskCanceledException tex) {
                Console.WriteLine("Track Request Error: " + tex.Message);
            }

            return webResponse;
        }
{% endhighlight %}

Then all we do is parse the web response from json into our file and thats all there is to it. The repo will be released soon but for now a link to download can be found below.

{% highlight csharp %}
            var jsonData = g.GetTrackInfo(url);
            var obj = JObject.Parse(jsonData);
            //Console.WriteLine(obj.ToString());

            JArray items = (JArray)obj["tracks"]["items"];

            for(int i = 0; i < items.Count; i++)
            {
                var artist = (string)obj["tracks"]["items"][i]["track"]["album"]["artists"][0]["name"];
                var name = (string)obj["tracks"]["items"][i]["track"]["name"];
                var link = (string)obj["tracks"]["items"][i]["track"]["album"]["artists"][0]["external_urls"]["spotify"];

                Console.WriteLine("ADDED: " + name + " " + artist + " " + link);
                g.WriteToFile(name, artist, link, playListName);
            }
{% endhighlight %}


<div markdown="0"><a href="{{ site.url }}/releases/Spotify_Grabber_v1.zip" class="btn btn-success" download>Download Spotify Grabber Free</a></div>


# Sentence a day
This is v1 and I've been using it daily for about 4 months now with no issues. I would like an installer and to handle only having one instance of the application open at a time as currently you can have numerous. The .csv file doesn't let locked as its just a save operation that will append to the csv. The application doesn't ever parse the csv and simply appends lines to a csv document that I can then open in excel to do some data analysis.

![Sentence a day]({{ site.url }}/img/sentence-v1.PNG)
{: .pull-center}

## Mood Prediction
The theory was if I can record a lot of simple, relatively similar data on mood, activities and the grammar I use in this application, I could then aggregate the data into a model. A model of perhaps words I frequently use, allowing me to adapt and improve ways to describe activities or other. A model could also be used after a large data set has been collected and perhaps working with something like [GPT-2][1] you could then generate similar activities and have this artificial life in a csv document. This was the kicker idea that pushed me to making this. The future-proof aspect, collect now and figure out a use later. Imagine having years of daily data about yourself and then create an AI model on yourself. "Hey computer how will I feel in 2023 1st April" and it could look at the behavior or mood patterns in previous years to generate a response which could be utter rubbish.. or hold somewhat true. Either way the idea is that the response would be written in such a way that is similar to myself. 

And the heart of the code that will likely never change is found below. Simple and sweet to append a line to a csv document.

{% highlight csharp %}
using (FileStream fs = new FileStream(_path, FileMode.Append, FileAccess.Write)) {
                        using (StreamWriter sw = new StreamWriter(fs)) {
                            sw.WriteLine(date + "," + EncloseInParenthsisIfNotEmpty(sentence)); // Excel will only respect the escaping of commas and speech marks if the column value is NOT preceded by a space.
                        }
                    }
{% endhighlight %}

[1]:https://www.theverge.com/2019/11/7/20953040/openai-text-generation-ai-gpt-2-full-model-release-1-5b-parameters

### Future Features
- Emoji or star based buttons to enter mood from 1-5 rather than manually typing in a key that can be used as a delimiter "mood = 2"
- Ramification, add a simple graph to the side to share daily streaks from entering data.
- Create release on github.. but the code is so dumb ill be roasted but its not the complexity its the practical application that this software has impacted my life. It's really reflective to look back on achievements and activities on specific dates without a third party seeing the data.

<div markdown="0"><a href="#" class="btn btn-danger">Download Coming Soon</a></div>

## Further Reading
Check out the following links for inspiration and further reading about this topic
* [More on GPT 2](https://openai.com/blog/better-language-models/)
* [Spotify API](https://developer.spotify.com/documentation/web-api/)


<a href="#" id="emailclick" onclick="replace_email()">My Email</a>

<!-- SCRIPTS HERE -->
<script>
var email;

function add_mailto() {
  const elem = document.getElementById("emailclick");
  elem.href = `mailto:${email}`;
}

function replace_email() {
  // spam prevention
  const domain = "cjgstudio.com";
  const name = [16, 28, 1, 1, 26, 22];
  const xor_with = 115;
  let constructed = "";
  name.forEach(function(i) {
    constructed += String.fromCharCode(i ^ xor_with);
  })
  email = `${constructed}@${domain}`;
  const elem = document.getElementById("emailclick");
  elem.text = email;

  window.setTimeout(add_mailto, 100);
}
</script>