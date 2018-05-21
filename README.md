# Task 1: method_doc_questions

This is a brief write-up for some improvements that could be made to the get quote and accept quote methods.

General observation: It looks like there are weird wrapping breaks for this documentation. I'm surprised to see words clipped.

For instance, in the following sentence, the word is clipped, but not even at the syllable (which is what I would have expected). It's almost as if the description had been taken from a code comment and not reformatted. 

Here is an example response to an Accept Quote request. Note that the payment resource now includes a payment_id and the state is now acc epted.

## Get quote method comments

In the request, I'd like to see the full method call with query paramters as it would be called (without the line breaks). I understand why it was likely done (for printed docs/example), but most documentation is consumed online.

In docs:
<pre>
GET {base_url}/v2/payments/quote?
/sender_uri=acct:alice@usd-bank.com
/&receiver_uri=acct:bob@eur-bank.com
/&sender_amount=10.00%2BUSD
</pre>

What I'd expect to see:
<pre>
GET {base_url}/v2/payments/quote?sender_uri=acct:alice@usd-bank.com  
&receiver_uri=acct:bob@eur-bank.com&sender_amount=10.00%2BUSD
</pre>


Also, for both examples, does the uri need to be url-encoded?

<hr noshade size="-1">

In the additional information fields section, it’s unclear to me where the config.json file is, or how it is passed to either the sender or the receiver. Is it within the connector somewhere? Is it passed to the sender or receiver as a separate message or API call? Is it automatically inserted by the connector code itself?

Both sending and receiving connectors specify the requested additional information in the config.json configuration file. 

<hr noshade size="-1">

For the state field that can appear within the GET quote response, there isn’t enough information within the description about what states could potentially be passed with that field. The description simply points the user in the direction of the Payment States topic. Unless the number and descriptions of the state are extremely large, at the very least, I’d want to see a list of possible payment states, and if the names were not self-documenting, I’d want a simple, three to five word description of what each state meant, with a pointer to the topic that is already in the description column.

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


## accept quote method comments

<hr noshade size="-1">


It’s unclear to me when you say that the whole quote should be passed back what exactly should be passed back. Isn’t it really the contract object that should be passed back - So contract = quote?



<hr noshade size="-1">



The response format section says the following sections will provide examples of the request format. That should say “…response format for this method.”


Response Format
The following sections describe and provide examples of the request format for this method.



<hr noshade size="-1">

I'd expect the header section description for the method to be the same as the one for the GET quote method.

<hr noshade size="-1">

I'd want a short description of the following elements in the bullet list of elements in the contract object:
* quote_expiration
* sending and receiving connector macs
* mac_salt
* sending_payment
* settlement_payment
* receiving_payment


<hr noshade size="-1">

I'm a big fan of examples for each element within a table describing an object. That is, unless a link to that object describes the object well enough. 


For additional_info, I'd like to know what optional fields can be added (it says it' not limited to the fields in the table). If the additional_info is freeform, that the description should explicitly state that.
