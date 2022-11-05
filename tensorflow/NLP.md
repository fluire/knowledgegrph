- ## sentiments in text
	- word encoding because its not possible to capture the meaning in letter encoding.
	- a simple tool to encode the word of a corpus of sentences
	- ![[Pasted image 20220925103927.png]]
	- `from tensorflow.keras.preprocessing.text import Tokenizer`
	- converting word to number is called tokenization.
- Text generation:
	- text -> convert to sentences -> sentences to tokens -> spliting x n y
	- where xs = seq[:,:-1] and label = seq[:,-1]
	- making label as one hot vector where the size of the vector is equal to the size of vocabulary so label 5 will be -> [0. 0. 0. 0. 0. 1. 0. 0. ......]
	- loss fn will be categorical_crossentropy.
	- embedding layer input_length <- max_seq_len - 1.
		- non bidirectional lstm -> generated text is repetative
		- bidirectional lstm -> converged faster and also have immunity against the repetation.
	- Using song for text generation
		- lines separated by separator->creating corpus by by getting list of lines->tokenizer initialization->fit_to_texts(corpus).
		- total word is equal to nuber of tokens+1 for padding token
		- now to create input and label 
			1. iterate over each line
			2. token_list <- convert it to token (texts_to_sequences)
			3. go over each token in the token_list and make sub phrases [2,3],[2,3,4],[2,3,4,5]..
			4. now separate into input and label [2,3]->[2]  [3] ,[2,3,4]->[2,3]  [4]
			5. then one hot encode the label tf.keras.utils.to_categorical(labels, num_classes=total_words)
			6. 
