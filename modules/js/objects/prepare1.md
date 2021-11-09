---
title: Objects - Representing Data
description: Representing complex data with objects
date: 2021-10-15

layout: layouts/post.njk
---

## Beyond Arrays

Arrays are wonderful things. If you need to keep several things of the same type together so you can work with them, an array is the way to go. But what about more complicated data? Consider this situation, you need to write code to track medications in a pharmacy. For each medication you need to track its name, the amount of the medication, its unique code, and expiration date. If you do this with arrays, your code could look something like this, the worst possible implementation.

```javascript
let names = ['Lactated Ringers','levothyroxine','rosuvastatin','albuterol','esomeprazole']
let amounts = ['100L','2000ct','1500ct','1325ct','23145ct']
let codes = ['13ab7','at342','gr5423','iuy6532','mnb78932']
let expDateDate = ['12/30/2029','03/18/2021','09/01/2020','01/01/2023','10/01/2021']
```

This code is intrinsically unstable. To work with this data, your code must keep track of and use the same index across all three arrays. However, as the data becomes more and more complicated, not just more data, the medication information will become corrupted. It is too difficult to keep everything straight; everything lined up, let alone passing this data to a function. Bugs will creap into this code and the application it is part of will fail.

Here is a slightly better way to solve this problem using a two dimentional array.

```javascript
let medications = [
	['Lactated Ringers','levothyroxine','rosuvastatin','albuterol','esomeprazole'],
	['100L','2000ct','1500ct','1325ct','23145ct'],
	['13ab7','at342','gr5423','iuy6532','mnb78932'],
	['12/30/2029','03/18/2021','09/01/2020','01/01/2023','10/01/2021']
]
```

This code is more organized, but has the same index and complicatedness problem as the first example, though it is easier to pass the data in this form to a function. However, when writing code using this data, you have to remember the order and indices of all the sub-arrays. This will be a constant problem as the data is passed, bugs fixed, and the data becomes more complicated. Thankfully, the creators of JavaScript provided a way out of this mess...defined objects.

## Defined Objects - keeping related data together

Defined objects allow us to mingle different types of data together, and build relationships between the data. Using the medication example, you could put a bunch of objects in an array. Each of these objects would hold one medication's name, its manufacturer, its best-by date, the amount of the medication on hand, and if that amount is a count or a volume in liters, milliliters, etc.

The way you would accomplish this in JavaScript is to apply the concept of a key-value pair. Being a BYU-Idaho student, you are familiar with key-value pairs already. Your iNumber is a key, and the data you supplied to the school about yourself is the value. Applying this concept to the medications data representation problem, a possible, though not optimal, solution looks like this, where id, amount, amountType, and expDate are the keys, and key-value pairs are seperated by commas.

```javascript
let lactatedRingers = {'id':'13ab7','amount':100,'amountType':'L','expDate':'12/30/2029'}
let levothyroxine = {'id':'at342','amount':2000,'amountType':'ct','expDate':'03/18/2021'}
let rosuvastatin = {'id':'gr5423','amount':1500,'amountType':'ct','expDate':'09/01/2020'}
let albuterol = {'id':'iuy6532','amount':1325,'amountType':'ct','expDate':'01/01/2023'}
let esomeprazole = {'id':'mnb78932','amount':23145,'amountType':'ct','expDate':'10/01/2021'}
```

To access the value associated with one of the keys, you use the name of the variable for the defined object and apply the key to look up the value.

```javascript
let anAmount = rosuvastatin['amount']
```
The variable anAmount would now contain 1500.

Changing a value works much like the code to modify a value in an array, but you would apply a key instead of using an array index.

```javascript
rosuvastatin['amount'] = 1455
```
Though this solution improves on the array representations, it suffers from having to pass each of the medications to functions that may work with or on the data. Also, it is easy to accidentally disconnect the medication names from their associated data. An additional layer of keys and values is needed to resolve this problem. In this solution, a defined object for all the medications contains other defined objects. This is much like a two dimentional array, an array that contains other arrays. Here, the name of the medication, with correct capitalization, is used as a key, and the data for that medication is the key's associated value.

```javascript
let medications = {
	'Lactated Ringers' : {'id':'13ab7','amount':100,'amountType':'L','expDate':'12/30/2029'},
	'Levothyroxine' : {'id':'at342','amount':2000,'amountType':'ct','expDate':'03/18/2021'},
	'Rosuvastatin' : {'id':'gr5423','amount':1500,'amountType':'ct','expDate':'09/01/2020'},
	'Albuterol' : {'id':'iuy6532','amount':1325,'amountType':'ct','expDate':'01/01/2023'},
	'Esomeprazole' : {'id':'mnb78932','amount':23145,'amountType':'ct','expDate':'10/01/2021'}
}
```
Another advantage of this organization of the data is there is no need to remember the order of the data. If you wanted all the data for Lactated Ringers, the code would look like this.

```javascript
let aMedication = medications['Lactated Ringers']
```
To get the same data for Lactated Ringers from the 2 dimentional array implementation the code would look like this,

```javascript
let aName = medications[0][0]
let anAmount = medications[1][0]
let anId = medications[2][0]
let anExpirationDate = medications[3][0]
```
a much less readable, intuitive, and debuggable solution.

Using the defined objects to get the expiration date for Albuterol without getting all the data for Albuterol, your code would look like this,

```javascript
let aBestByDate = medications['Albuterol']['expDate']
```
where getting it using the 2 dimentional array implementation would look like this.
```javascript
let aBestByDate = medications[4][4]
```

To change the amount of Rosuvastatin on hand, the code would look like this,

```javascript
medications['Rosuvastatin']['amount'] = 1432
```
instead of like this, using the 2 dimentional array.

```javascript
medications[2][3] = '1432ct'
```

## There is Another Way

When you have defined objects, there is another way to access and change values. It uses what is called 'dot notation' by the JavaScript community. Let's look at the example where the amount of Rosuvastatin was changed again. You could do it like this.

```javascript
medications.Rosuvastatin.amount = 1432
```
That's kind of nice. Many fewer characters to type. You drop all the brackets and quotation marks. But can you use dot notation to set a value? Yep. You can. Here is the Albutorol example from earlier rewritten using dot notation.

```javascript
let aBestByDate = medications.Albuterol.expDate
```
It may seem that, because dot notation is so much less wordy, it should always be used. Not so fast. There are times when it doesn't work. It only works when you know what the keys are at the time you are writting your code. Let me explain.

Suppose you had a user interface where the user selected the name of the medication to display the expiration data for. Now you have a problem. You have to put what the user selected into a variable in order to be able to use it. Let's say you put it in a variable called 'selectedMedication'. The temptation is to think that this code would work.

```javascript
let aBestByDate = medications.selectedMedication.expDate
```
It doesn't. This code does work though.

```javascript
let aBestByDate = medications[selectedMedication]['expDate']
```
This code works too. It combines both approaches and is probably the cleanest code to solve this problem.
```javascript
let aBestByDate = medications[selectedMedication].expDate
```
If nothing else, JavaScript is very flexible. So which one should you use? It depends on which works to solve the problem you are working on. Pick the one that is the simplest for any given situation.