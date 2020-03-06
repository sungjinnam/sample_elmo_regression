# Keras+ELMo regression

This notebook is a sample code of using Keras and ELMo (<https://tfhub.dev/google/elmo/2>) to predict the informativeness score of sentences.
*Note: This code sample does not contain the sentence data or model weights.*
*Note: The notebook only contains the preliminary testing results of lager work.*

## Input

Single sentence formatted for ELMo (e.g., using *< BOS >* and *< EOS >* tokens to indicate the beginning and end of each sentence). The model also assumes using a cloze sentence (i.e., a sentence with a blank) as input. The cloze target is indicated as blank (_____).

## Model

The notebook contains a simple DNN regression model.
One thing to notice is that unlike the original ELMo's LSTM layer outputs, we customized the ELMo embedding layer to extract the contextual information as a single vector, concatenating the L->R vector before the cloze target, and the L<-R vector after the target word.

## Output

The dependant variable contains continuous numeric values. This is based on the human annotations that we did not include in this sample code repository. For the quick comparison, we used Spearman's *r* to evlauate the prediction performance.