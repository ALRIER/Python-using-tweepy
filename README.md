# Python-using-tweepy

# -*- coding: utf-8 -*-
"""
Editor de Spyder

Este es un archivo temporal.
"""

import tweepy
import json

'''ive to write my authentication keys'''
consumer_key= "jAPg5z6x0rwLVh5MsN8kwqL13"

consumer_secret = "osgxg44woM06z0JxaaLrzYaic5UZEgDglxGBZOOuJTrLeNKJQy"

access_token ="284827529-2vFzx1DeskheeibMllHv1LoKZiTbvALlltVxawA2"

acess_toke_secret ="kGw0JdHPiWJ7F6qSr6o4elyOoLo99auykQBdzQ7ZZrigW"

'''i create the authentication proces with the keys'''
auth = tweepy.OAuthHandler(consumer_key, consumer_secret)
auth.set_access_token(access_token, acess_toke_secret)

'''I create the authentcation call with an special command 
to avoid that the call goes down after 15 minutes'''
api = tweepy.API(auth, wait_on_rate_limit = True,
                 wait_on_rate_limit_notify = True)
'''the is an auto tuthentication protocol to verify
everithyng is ok'''
#data = api.me()
#print (data)

'''con este comando obtengo el barrido de 
información deuna cuenta, donde me descarga un moneón de información del 
perfil, con nombre de usuario, con identificación, color que usa en el 
perfil, ubicación, entre otros datos del perfil'''

#data1 = api.get_user("CarlosSantiagoL")
#print(data1)

'''ahora voy a obtener los folowers de carlos santiago'''
#data3 = api.followers(screen_name="CarlosSantiagoL")
#for user in data3:
    #print(data3)
'''con este len me doy cuenta de que solamente extrajo 20 datos de seguidores,
esto se debe a que las API solamente extraen un determinado número de lladas, 
pero existe una solución'''
#print(len(data3))

'''cursor es un comando que permite llamar cuantos datos yo desée'''
'''en este caso dentro de Cursor, el primer comando es el metodo que voy a 
usar, que en este caso será api.followers, pero puede ser cualquier otor,
'''
#for user in tweepy.Cursor(api.followers, screen_name="CarlosSantiagoL").items(10):
    #print (user)
    
#user1= json.dumps(user._json, indent=2)


'''ahora voy a obtener el timeline de una persona "CarlosSantiagoL",
esta persona por ejemplo.'''

for tweet in tweepy.Cursor(api.user_timeline, screen_name="CarlosSantiagoL", tweet_mode="extended").items(200):
