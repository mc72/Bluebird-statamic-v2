# BlueBird by [Nick Snyder](http://nicksnyder.is)
## A Twitter plugin for Statamic CMS V2.x
## Contributions by [Jason Varga](http://pixelfear.com)
## converted to Statamic V2.x addon by [Mike Ciccone](http://www.adnetinc.com)

BlueBird is a Twitter API 1.1 plugin for the Statamic CMS v2.x. With BlueBird, you can pull down a predefined number of tweets from any user with publicly available tweets. BlueBird automatically coverts hashtags, URLs, and mentions into their appropriate links. 

To get started, simply upload the folders to the appropriate directories. If you haven't registered for a Twitter API, you may [do so here](http://dev.twitter.com). After you obtain your Access Token, Access Token Secret, Consumer Key, and Consumer Secret, add them to "/site/addons/Bluebird/default.yaml". That's it!

### Support

I did not write the original code, just converted this to a Statamic V2 addon.

### Example Code Block

    {{ bluebird screen_name="_nicksnyder" count="1" }}
			{{ tweets }}
				<div>
					<p>{{ text }}</p>
					<p>
						<small>
							<a href="{{ tweet_url }}">{{ created_at format="F jS, Y" }}</a>
						</small>
					</p>
				</div>
			{{ /tweets }}
			{{ user }}
				<div>
					<a href="https://twitter.com/{{ screen_name }}">
						<img src="{{ profile_image_url }}" alt="{{ screen_name }} on Twitter">
						Follow Me on Twitter!
					</a>
					<ul>
						<li>{{ followers_count }} Followers</li>
						<li>Listed {{ listed_count }} times</li>
					</ul>
				</div>
			{{ /user }}
    {{ /bluebird }}

### Documentation

#### Parameters

* **screen_name**: Screen name of the user who's tweets you'd like to display; no @ symbol, please. (string) [ *Required* ]
* **count**: Number of tweets you'd like to display (number) [ *Default: 5* ]
* **include_rts**: Option to include retweets as part of your count (boolean *true*, *false*) [ *Default: true* ]
* **include_entities**: Option to automatically convert entities into live links (boolean *true*, *false*) [ *Default: true* ]
* **cache**: How long to cache the API response in seconds (number) [ *Default: 60* ]

#### Tag Pairs & Variables

BlueBird contains two tag pairs: {{ tweets }} and {{ user }}.

The {{ tweets }} tag pair allows you access to everything in the Twitter API. Using the Statamic shorthand of {{ level1:level2 }}, you can access nested arrays.

* {{ created_at }} - Echos the creation date of the tweet; You may use PHP's date functions to format (e.g. {{ created_at format="F jS, Y" }} )
* {{ id }} - ID of the tweet in number format
* {{ id_str }} - ID of the tweet in string format
* {{ text }} - Actual tweet
* {{ tweet_url }} - a pre-built URL for each tweet
* {{ source }} - Client used for the tweet
* {{ retweet_count }} - Amount of times the tweet has been retweeted
* {{ favorited }} - Amount of times the tweet has been favorited
* {{ retweeted }} - Returns true if tweet was a retweet, rather than original
* {{ user:id }} - ID if the user in number format
* {{ user:id_str }} - ID if the user in string format
* {{ user:name }} - Full name of the user
* {{ user:screen_name }} - User's Twitter handle
* {{ user:location }} - User's location (per the profile, rather than tweet)
* {{ user:url }} - User's URL
* {{ user:description }} - User's description
* {{ user:protected }} - Returns true if the user has a protected account
* {{ user:followers_count }} - Number of followers
* {{ user:friends_count }} - Number of friends
* {{ user:listed_count }} - Amount of times the user has been lsited
* {{ user:created_at }} - User's join date
* {{ user:favourites_count }} - Amount of favorites the user has
* {{ user:time_zone }} - User's Time Zone
* {{ user:verified }} - Returns true if the user has a verified account
* {{ user:status_count }} - Number of tweets
* {{ user:profile_image_url }} - URL of the user's profile image

The {{ user }} tag pair allows you to return just user data without displaying tweets.

* {{ id }} - ID if the user in number format
* {{ id_str }} - ID if the user in string format
* {{ name }} - Full name of the user
* {{ screen_name }} - User's Twitter handle
* {{ location }} - User's location (per the profile, rather than tweet)
* {{ url }} - User's URL
* {{ description }} - User's description
* {{ protected }} - Returns true if the user has a protected account
* {{ followers_count }} - Number of followers
* {{ friends_count }} - Number of friends
* {{ listed_count }} - Amount of times the user has been lsited
* {{ created_at }} - User's join date
* {{ favourites_count }} - Amount of favorites the user has
* {{ time_zone }} - User's Time Zone
* {{ verified }} - Returns true if the user has a verified account
* {{ status_count }} - Number of tweets
* {{ profile_image_url }} - URL of the user's profile image


### MIT License

Copyright (c) for original plugin code 2013–2104 Nick Snyder

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
