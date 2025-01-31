# Some definitions
## Options:

1. Identifier
2. Description
3. Summary
4. Summary is editable (true or false)
5. Amount
6. Amount is editable (true or false)
7. Minimum age
8. Payment timeout
9. OTP device

## Taler Docs Info:

The template is a backend feature that is used to allow wallets to create an order. This is useful in cases where a store does not have Internet connectivity or where a Web site wants to enable payments on a purely static Web page (for example to collect donations). In these cases, the GNU Taler wallet can be used to set up an order (and then of course pay for it).

The template itself primarily provides order details that cannot be changed by the customer when the wallet creates the order. The idea is that the user may be prompted to enter certain information, such as the amount to be paid, or the order summary (as a reminder to themselves or a message to the store), while the template provides all of the other contract details.

The typical user experience with templatates is that the user first scans a QR code or clicks on a taler://-URI which contains a pay-template (see LSD 0006). The URI specifies which values the user should supply, currently either nothing, the amount, the order summary, or both. The URI may also specify defaults or partial defaults for those values. After the user has supplied those values, the wallet will use the public template API to create the order, then fetch the order details, and proceed as if it had been given the respective pay URI in the first place: show the full contract details and allow the user to make a payment. If the user chooses to abort the payment, the wallet should give the user the opportunity to edit the values and create another order with different values. If the template does not include any values that the user is allowed to edit (so it is basically a fixed contract), the wallet should directly create the order and immediately proceed to the contract acceptance dialog.

The business process for the templating API is also pretty simple. First, the
private API is used to setup (or edit) the template, providing all of the
contract terms that subsequently cannot be changed by the customer/wallet.
This template data is then stored under the template ID which can be freely
chosen and must be in URL-encoded format. The SPA should also make it easy
for the merchant to convert the template ID into a taler://-URI and/or QR code.
Here, the merchant must additionally specify the defaults (if any) for the
customer-editable values. Afterward, the merchant can print out the QR code
for display at the store, add a link to the taler://-URI and/or embed the
respective QR-code image into their Web page.


To receive a payment confirmation, the merchant may choose to configure a webhook in the merchant backend on the pay action, for example, to send an SMS to their mobile phone. For points-of-sale without a mobile phone or Internet connectivity, the OTP mechanism can also be used to confirm payments.

## Possibilities
1. Add template
2. See the URL in the QR code format
3. Print it
4. Put it in the store
---
This block runs in the loop
5. Customer can pay (optionally modify the receipt if allowed by merchant)
6. Customer wait for the merchant to see the payment, or SMS, or to check if the OTP matching.
---
8. Delete the template

## Scenes

1. Taler Backoffice
2. Store (extended version)

## Actors

1. Instruction voice
2. Merchant (extended version)
3. Buyer (extended version)

# Script

## **Video Plan: Templates Guide**

### **1. Introduction**
- **Visuals**: Animated title screen with "Templates Guide".
- **Voiceover**:
    - "Welcome, everyone! Today, we'll guide you through the templates feature. From setup to usage, we've got you covered."
- **Scene**: Show a merchant setting up a QR code at their store and a buyer using it to pay.

### **2. What are Taler Templates?**
- **Voiceover**:
    - "Templates in Taler allow wallets to create pre-defined orders for payments. 
These are ideal for payments without internet connectivity or for static websites."
- **Visuals**:
    - Animation or diagram explaining the concept of templates. (or)
    - Example of a static webpage showing a payment link.
- **Visuals Extended Version**:
    - A customer enters a shop, scans the QR code, modifies the amount or summary (if editable), and pays. 
Merchant receives confirmation via SMS or OTP.

---

### **3. How to Add a Template**
#### **3.1 Access the Taler Backoffice**
- **Visuals**:
    - Screen capture of opening the Taler Backoffice main view.
    - Navigation to the "Templates" section.
- **Voiceover**:
    - "First, access the Taler Backoffice and navigate to the 'Templates' page."

#### **3.2 Create a New Template**
- **Visuals**:
    - Click on the "+" (plus) button to create a new template.
    - The form opens.
- **Voiceover**:
    - "Click on the 'Add Template' button to create a new template."

#### **3.3 Fill in the Template Form**
- **Visuals**:
    - Highlight fields: Identifier, Description, Summary, Amount, Minimum Age, etc.
    - Emphasize the "Summary is editable" and "Amount is editable" options, as well as "OTP Device" (super optional).
    - Screen capture of toggling these options on/off and explaining their functionality.
- **Voiceover**:
    - "Fill out the form with your desired options. You can choose whether the summary and amount are editable by the customer."
- **Extended Version**:
    - Show a buyer's perspective of editing fields like summary and amount and completing a transaction.
    - Show how does the OTP looks like from the perspective of the user

#### **3.4 Save the Template**
- **Visuals**:
    - Screen capture of pressing the "Save" button.
- **Voiceover**:
    - "Once you're done, click 'Save' to add the template."

---

### **4. How to View the Template**
#### **4.1 Generate and View QR Code**
- **Visuals**:
    - Open the Templates page.
    - Click the QR button to view the code.
    - Show the displayed QR code.
    - Options to print the QR code or embed it in a webpage.
- **Voiceover**:
    - "To view the template, navigate to the Templates page and press the QR button. 
    This opens a scannable qr-code for your template. You can print the QR code or add it to your website for easy customer access. 
    Also you can copy the link to put it on your website"

---

### **5. How to Delete a Template**
- **Visuals**:
    - Navigate to the Templates page.
    - Highlight and click the Delete button.
    - Confirmation dialog appears.
- **Voiceover**:
    - "To delete a template, go to the Templates page, hover over the template, and click the Delete button."


### **7. Closing**
- **Visuals**:
    - Animated outro with the Taler logo and a thank-you message.
- **Voiceover**:
    - "That’s it for our guide on Templates. Thank you for watching, and happy templating with Taler!"
- **Call to Action**:
    - "For more information, visit our website or check out our documentation."

