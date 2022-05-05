# Python-using-tweepy

# -*- coding: utf-8 -*-
"""
Editor de Spyder

Este es un archivo temporal.
"""
#i have to import my tweepy and json to take a look of the information. 
import tweepy
import json

#ive to define my authentication keys
consumer_key= 

consumer_secret = 

access_token =

acess_toke_secret =

#now i can make all the autentication process using the OAuth from tweepy
auth = tweepy.OAuthHandler(consumer_key, consumer_secret)
auth.set_access_token(access_token, acess_toke_secret)

#I create the authentcation call with an special command to avoid that the call falls down after 15 minutes
api = tweepy.API(auth, wait_on_rate_limit = True,
                 wait_on_rate_limit_notify = True)
                 
#this is an authentication protocol to verify everithyng is ok
#data = api.me()
#print(data)

#con este comando obtengo el barrido de 
#información deuna cuenta, donde me descarga un moneón de información del 
#perfil, con nombre de usuario, con identificación, color que usa en el 
#perfil, ubicación, entre otros datos del perfil

#Now i will get the user information, in my case is just an example to see if it works propperly. 
#data1 = api.get_user("CarlosSantiagoL")
#print(data1)

#Now i want to know the followers of the user. 
#data3 = api.followers(screen_name="CarlosSantiagoL")
#for user in data3:
    #print(data3)

#con este len me doy cuenta de que solamente extrajo 20 datos de seguidores,
#esto se debe a que las API solamente extraen un determinado número de lladas, 
#pero existe una solución

#With the comand len i can take a look about how many information it downloaded.
#i can see that the api just called 20 tweets, but i can use other comands to solve this problem. 
#print(len(data3))

# "cursor" es un comando que permite llamar cuantos datos yo desée. 
# En este caso dentro de "Cursor", el primer comando es el metodo que voy a usar, que en este caso será api.followers, pero puede ser cualquier otor,

# "cursor" is an option to solve it, becouse i can tell the computer how many idems i want to download. 
#for user in tweepy.Cursor(api.followers, screen_name="CarlosSantiagoL").items(10):
    #print (user)
    
as i previusly have created the object "user", now i will set it as json format to check the information. 
#user1= json.dumps(user._json, indent=2)


#now i can use the same comand "cursor" to download 200 items from the timeline of an user, in my case, the same person. 

for tweet in tweepy.Cursor(api.user_timeline, screen_name="CarlosSantiagoL", tweet_mode="extended").items(200):
