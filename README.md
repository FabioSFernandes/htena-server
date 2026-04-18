Hello guys, I am a little bit crazy a computer scientist and I love to play with SD. Dealing with a computation problem and limitation, I was testing some approach to allow me to work with high tokens density exchange without having to "buy" more memory or a incredible GPU (maybe tranfering it to a cloud vendor easily). This approach is an easy way, based in our current availability solutions in the market, I would say also a natural tendency, to turn easier to deploy AI solutions. 

The idea é allow anyone to deploy the high processing part to a GPU vendor or UM vendor, without changing entire infrastruture from the current cloud or on-premise server. 

I am calling it just to turn ir as a simple reference to the concept. 

# htena-server
High Density Tokens Exchange Network Agnostic - tokens as a service 

## Introduction 

It is a proposal solutions to decouple IA solutions from hardware, but at the same time, it estimulates use of remote hardware like cloud computing hardware. With this, part of your AI solution can solve vocabulary resolution problems, and the allocated service is responsible remotelly for tokens processing. It also helps to protect how your solution deal with information from hardware vendor providers, that will simply process tokens and exchange it with the client.  

## Use case
Today we have the challenge of having entire llm engine running in a very special and expensive hardware. If you need to create a service, this service needs the infrastructure close to it. You have some problems to solve: 

- You need just the cpu and vram, but you must allocate entire llm solution 
- If you need LLM, it take you to deploy a significant part of your solution to an infrastructure
- The most expensive part os processing is the LLM processing most of times 
- You want to choose infrastructure provider, but you still do not trust it too much to deploy your total solution
- You can distribute your solution across different network providers, with aproppriate newtwork settings for safety and reaching
- For high processing needs from Edge solutions: robotics, medicinal, and other uses, the ai processing costs are very expensive beyond real feature developed, hardware focus should be specific to functionality. LocalAi processing turns it more expensive because you have to plan higher hardware costs to process things locally. 

##Solution approach high level

______________________________________________________________________________________________________________________
|                                 |                                         |                                        | 
|           Any client            |           Exchange negociation          |       Server provider infrastruture    | 
|_________________________________: ________________________________________:________________________________________|
|                                 :                                         :                                        |
|--------------------------|      :          |---------------------|        :        |------------------------|      |
|                |-------| |-<<----------->>-|  LLMm neggotiation  |--<<---------->>-| hdte compatible server |      |
|   Edge device  |       |-|      :          |---------------------|        :        |------------------------|      |
|                |  hdte | |      :                                         :              |  Well managed energy    |
|                |  cli  | |      :          |---------------------|        :              |  Hardware providers     |
|                |-------| |-<<--------------|   Tokens streaming  |--<<-------------------|  Sell tokens processing?|
|--------------------------|      :          |---------------------|        :                 Tokens as a service    |
|                                 :                                         :                 Remote HW transfer     | 
|                                 :                                         :                 Concerns splitting     | 
|                                 :                                         :                 Easy portability       | 
|____________________________________________________________________________________________________________________|


## layers

- hdten or hdten client
Is theconsumer, initializer and token final user. It knows how to decode and use the tokens

- LLM Negociation and Streaming 
The protocol itself. It turns the token as a service a feasible and stable solution

- htde compatible server
Simply a server that runs a hdte server, witha list of local or routed models (anthropic for exaqmple) 


## Comunication process 
Premise: The client knows server url, and know how to authenticate into it. It can be vendor specific and does not impact hdte message exchange. 
The client can be running in a browser with javascript, for example, and start protocol asking for server capabilities. If server allows on-demand models, the client can ask fora  model load, and send a webhook to start getting tokens. Also the server could answer "hey, i dont have webhook, start listening here <protocol>:<auth>@<address>" (for example). 
In bth cases client will be waiting for the tokens assinchronously. Then the hdte server can start sending raw tokens and then send final tokens mark (EOS) to stop streaming. 

message author               ->>>>            destination                    
1.client(adress,auth)         ->>>>            server 
2.server(capabilities, 
  ondemand async/
  starts imediatelly, 
  webhook/connect-and--wait)   ->>>>            client 
3.client(ask for models)       ->>>>            server 
  server(models list, vocabs, 
  urls, token resolution 
  resources)                   ->>>>            client 
4.client("execute/order" 
  a model, send webhook)       ->>>>            server 
5.server(load llm,
  prepare webhook/
  wait streaming)              ->>>>             client 
6.client(wait)                 ->>>>             server 
7.server(intense streaming)    ->>>>             client(vocab/detokenize) 

Today we have some people around the world testing it with me, I will go ahead with discussions and acceppt suggestions.
I believe it is also a natural tendence and probably there are other people thinking in how to solve problems like this.










