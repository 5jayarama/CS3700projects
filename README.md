What the program does:
This is a client program that plays the game wordle. It connects to a server which picks a five letter word out of a word bank,
and the client must guess this word. After a guess, the program will send information on how close the guess is. Once the client
correctly guesses the word, the server will return a secret flag that shows the program ran successfully, which the client will display. The client plays the game for you. The user does not play.

This program has the option to use TLS encrypted sockets or TLS non-encrypted sockets to communicate with the server. Each option
has a different secret flag. If the client is using TLS encryption, it will be indicated with a print statement

What arguments to input:
the user should input an arguement in this format: ./client <-p port> <-s> <hostname> <Northeastern-username>
Do not include the <> signs. the <-p port> is optional, otherwise the program will use the default port. The <-s> is optional,
and only include if you want to use TLS encrypted messages. The <hostname> and <Northeastern-username> are mandatory inputs.
The hostname should be proj1.3700.network, because that is the server we connect to.
Here is an example arguemnt: ./client -s proj1.3700.network jayaram.ad

Strategy for improving performance:
I store a custom list of words that the client can choose from. when the wordle program first runs, the list is the same as the 
list in the project1-words.txt file. After each loop, the list is reduced based on the marks array that we recieve in the retry message. I check each word in the wordlist, and check if it matches the specifications in the marks array. This involves checking each letter in the word against each number in the marks array. I then return a new filtered list, with only the valid words. This way, I minimize the number of sends and receives to the server. Finally, when I get the correct word, and the bye response message, I print the secret flag. 
