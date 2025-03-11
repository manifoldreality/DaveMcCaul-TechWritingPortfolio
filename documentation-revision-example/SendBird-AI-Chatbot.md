# Docs for SendBird AI Chatbot for Healthcare

https://sendbird.com/developer/tutorials/how-to-build-an-ai-chatbot-for-healthcare

## Synopsis of Changes
I was surprised there were no sample screenshots for these three UI displays! I included the three screenshots upfront and linked them to the relevant instructions for setting up each one. Including the screenshots also allowed me to remove a lot of superfluous text (seen in strikethrough). The code snippets are probably the most important part of the instructions, but the snippets were large enough that I linked to them elsewhere (ideally this would be done using an anchor link). This left me with a much more concise outline/overview which I believe would suffice for a developer audience.   

### ORIGINAL TEXT/STRUCTURE

**UI components for your AI chatbot for healthcare**
You can display the following UI components in your healthcare AI chatbot’s conversation interface.
**CardView**
The data in the response are displayed in a Card View. In the demo, information such as the provider’s details can be displayed in a card with an image, title, and description. Customization of the view can be done through cardViewParamsCollectionBuilder and SBUCardViewParams. The following codes show how to set up a Card View:
* imageURL: The URL of the image to be displayed on the card
* title: The title to be displayed on the card
* subtitle: The subtitle to be displayed on the card
* description: The description to be displayed on the card
* link: The link to be displayed on the card (If actionHandler is set, link is ignored.)
* actionHandler: The action to be performed when the card is clicked

**QuickReplyView**
The following codes demonstrate how to set the view for Quick Replies. The values in options of first_message_data.data are used as Quick Replies. When the user clicks on Quick Reply, the message is sent to the server.

**ButtonView**
The following code demonstrates how to set the view for Buttons. When the server returns a response that includes the information of adding a button to call the action, by setting the SBUButtonViewParams and updateButtonView(with: buttonParams), the button is displayed in the message. The following codes show how to set the Button view of the doctor reservation.
* actionText: The text to be displayed on the button
* description: The text to be displayed below the button
* actionHandler: The action to be performed when the button is clicked
* enableButton: Whether the button is enabled or not
* disableButtonText: The text to be displayed on the button when it is disabled

###REVISED TEXT/STRUCTURE
**UI components for your AI chatbot for healthcare**
Choose from the following display types for your healthcare AI chatbot’s conversation interface:
| Display Type   | How it Looks  |
| --------       | ---------     |
| [CardView](#cardview)       | UI Screenshot |
| [QuickReplyView](#QuickReplyView) | UI Screenshot |
| [ButtonView](#ButtonView)     | UI Screenshot |

**<a name="cardview"></a>CardView**
~~The data in the response are displayed in a Card View. In the demo, information such as the provider’s details can be displayed in a card with an image, title, and description. Customization of the view can be done through~~
**How to Customize:**

cardViewParamsCollectionBuilder and SBUCardViewParams 

**Display Components (click here for full code sample)**

* imageURL: ~~The URL of the image to be displayed on the card~~
* title: ~~The title to be displayed on the card~~
* subtitle: ~~The subtitle to be displayed on the card~~
* description: ~~The description to be displayed on the card~~
* link: ~~The link to be displayed on the card~~ (If actionHandler is set, link is ignored.)
* actionHandler: The action to be performed when the card is clicked

**<a name="QuickReplyView"></a>QuickReplyView**
~~The following codes demonstrate how to set the view for Quick Replies. The values in options of first_message_data.data are used as Quick Replies. When the user clicks on Quick Reply, the message is sent to the server.~~

**How to Customize:**
Change the values in options of first_message_data.data 
Components (click here for full code sample)

**<a name="ButtonView"></a>ButtonView**
~~The following code demonstrates how to set the view for Buttons. When the server returns a response that includes the information of adding a button to call the action, by setting the~~

**How to Customize:**
SBUButtonViewParams and updateButtonView(with: buttonParams)~~, the button is displayed in the message. The following codes show how to set the Button view of the doctor reservation.~~

**Components (click here for full code sample)**
* actionText: The text to be displayed on the button
* description: The text to be displayed below the button
* actionHandler: The action to be performed when the button is clicked
* enableButton: Whether the button is enabled or not
* disableButtonText: The text to be displayed on the button when it is disabled
