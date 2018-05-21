# Task 1: method_doc_questions


In the additional information fields section, it’s unclear to me where the config.json file is, or how it is passed to either the sender or the receiver. Is it within the connector somewhere? Is it passed to the sender or receiver as a separate message or API call? Is it automatically inserted by the connector code itself?

Both sending and receiving connectors specify the requested additional information in the config.json configuration file. 

<hr noshade size="-1">

For the state field that can be passed within the quote, there isn’t enough information within the description about what states could potentially be passed with that field. The description simply points the user in the direction of the Payment States topic. Unless the number and descriptions of the state are extremely large, at the very least, I’d want to see a list of possible payment states, and if the names were not self-documenting, I’d want a simple, three to five word description of what each state meant, with a pointer to the topic that is already in the description column.

The state of the payment. See Payment States for more information. 

<hr noshade size="-1">

I would want the terms object spelled out more, unless the terms are completely free-form, bespoke objects, but I don’t believe that to be the case. I understand that some terms *might* be specific to the transaction, but the below object seems pretty straightforward.

<pre>
"terms":{
    "sending_fee":{
      "value":"0.0366050704224261",
      "currency":"EUR"
    },
    "fx_rate":{
      "base":"EUR",
      "counter":"GBP",
      "rate":"0.6826923076943427"
    },
    "receiving_fee":{
      "value":"0.049",
      "currency":"GBP"
    }
  },
</pre>
<hr noshade size="-1">

It’s unclear to me when you say that the whole quote should be passed back what exactly should be passed back. Isn’t it really the contract object that should be passed back - So contract = quote?

<hr noshade size="-1">



In the accept quote method documentation, the response format section says the following sections will provide examples of the request format. That should say “…response format for this method.”


Response Format
The following sections describe and provide examples of the request format for this method.
