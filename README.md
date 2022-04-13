# Write-UP-WEB-SDR-HackDay
Dans ce Writeup, je vous explique comment j'ai réussi à flag le challenge du CTF [Hackday](https://hackday.fr/)


<img width="400" alt="Capture d’écran 2022-04-13 à 15 19 06" src="https://user-images.githubusercontent.com/39098396/163189411-4b3035a6-22a9-434a-8daf-92e0781c2fc6.png">

Ce chall ne fourni ni fichier ni ip/port pour du tcp, mais le titre donne un indice "WebSDR" :  
Un WebSDR est un récepteur radio accesible sur Internet, nous permettant ainsi d'écouteur et d'analyser certains signaux sans forcément avoir le materiel nécessaire. 
Certain site web comme http://websdr.org/ permet de les lister 

Le challenge est hebergé par ESIEE Paris donc une plateforme francais, il conviendra donc de selectionner un websdr hebergé proche de paris : 
celle ci par exemple : http://dk0te.dhbw-ravensburg.de:8901/

<img width="600" alt="Capture d’écran 2022-04-13 à 16 01 04" src="https://user-images.githubusercontent.com/39098396/163197774-5cc4130d-c32d-46b4-89c6-7e4b99ad9aab.png">

En journée, le signal va etre moins audible voir quasi inexistant en cas de forte température. Ce sont les lois de la Propagation ionosphérique, ainsi, il vaut mieux écouter le signal en soirée. (Comme le dis l'énoncée : A la nuit tombée, tout s'éclaire)


Une fois le signal enregistrée : 

<img width="600" alt="Capture d’écran 2022-04-13 à 16 01 04" src="https://user-images.githubusercontent.com/39098396/163225165-9a5ca4ba-85d3-4278-9c3c-7e2198882a94.png">

Rien de flagrant, mais avec audacity nous pouvons afficher le spectre et en jouant avec les réglages du spectograme, le logiciel peut afficher données assez intérressantes : 

<img width="600" alt="Capture2d’écran 2022-04-13 à 16 01 04" src="https://user-images.githubusercontent.com/39098396/163226553-40229a61-16ef-4b6b-8f0c-10a62abf6cba.png">

Maintenant nous pouvons prendre un fichier texte et commencer à réecrire bits par bits. 
Il y à quand meme quelques indices pour pas commencer n'importe ou et sans repères : 
Nous savons que le flag commence par "HACKDAY{" donc : 
```
01001000 01000001 01000011 01001011 01000100 01000001 01011001 01111011
H        A        C        K        D        A        Y        {         
```
Nous pouvons également voir la présence de bits de synchro  :   
![synchro](https://user-images.githubusercontent.com/39098396/163229211-e6eae77f-1e2e-4f4a-ade2-1db7d16253bf.png)



Nous pouvons donc en déduire que notre signal commence juste après la synchro. 

Chaque charactère Ascii (sous forme de 8bits) sont séapré par 4bits 'x110' (faisant parti du protocole)   

![bitssynchro](https://user-images.githubusercontent.com/39098396/163234116-d49f9353-a5a0-4798-9d1d-b291f0779404.png)

Une fois compris la mécanique de la trame, il suffit de décoder jusqu'a la fin du flag soit '}'
![bits](https://user-images.githubusercontent.com/39098396/163230726-a3db75fd-f66e-403e-a94f-b960b717ca24.png)

```
0101010101010100010010000110010000010110010000111110010010110110010001000110010000010110010110010110011110110110001101001110001110001110001011100110001110001110001101001110001100001100011001101100011001011100010110011100011001011100010111001100011010101100011100011100011001101100011000011000111001011000110101011001111101011001000110111000
```
**HACKDAY{48.84032,2.583095}**
