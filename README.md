import tweepy

# Replace these with your own API keys and tokens
consumer_key = "your_consumer_key"
consumer_secret = "your_consumer_secret"
access_token = "your_access_token"
access_token_secret = "your_access_token_secret"

# Authenticate with Twitter API
auth = tweepy.OAuthHandler(consumer_key, consumer_secret)
auth.set_access_token(access_token, access_token_secret)
api = tweepy.API(auth)

# Function to scrape tweets
def scrape_tweets(username, num_tweets=10):
    try:
        # Get user timeline tweets
        tweets = api.user_timeline(screen_name=username, count=num_tweets)

        for tweet in tweets:
            print(f"Tweet: {tweet.text}")
            print(f"Created at: {tweet.created_at}\n")

    except tweepy.TweepError as e:
        print(f"Error: {str(e)}")

if __name__ == "__main__":
    username = "TwitterUsername"  # Replace with the username you want to scrape
    num_tweets = 10  # Number of tweets to scrape (adjust as needed)
    scrape_tweets(username, num_tweets)
