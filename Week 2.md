# Using TinkerCad
Now that you have opened TinkerCad it is time for you to learn how to use it.
## Opening your new circuits file
Try looking at the tab on your left-hand side. You will be able to find this tab on the picture below.<br>
<img src="./images/1.png" alt="drawing" width="200"/><br>
On that tab, click "Circuits". Once you click "Circuits", you would see a new function called "Create New Circuit". Clcik on it and let the magic begin! <br>
<img src="./images/2.png" alt="drawing" width="200"/><br>
## Creating your circuit
First of all, it looks overwhelming isn't it? Have a look at your new space. You can see that on the right, you would be able to see all the basic components.<br>
<img src="./images/3.png" alt="drawing" width="300"/><br>
With that, simply just click and drag the components that you need. If you need to find a component, simply search it up, just click on the search bar on the tab. For example, if you wish to insert an Arduino, search up 'Arduino' and drag it as shown in this picture. <br>
<img src="./images/6.png" alt="drawing" width="200"/><br>
And don't forget to create your circuit! Try placing an Arduino and a breadboard beside each other. To create a wire, click on one of the holes from either the Arduino or the breadboard and link it to the other preferred hole. <br>
<img src="./images/7.png" alt="drawing" width="200"/><br>
Oh and if you need to change the colours of the wire, don't fret! Look at the tab above and you could see this option. By convention, ground wires are black and Vcc wires are red.<br>
<img src="./images/8.png" alt="drawing" width="200"/><br>
You would be able to change the wire colour and the wire type from there.<br>
Here is the example circuit that you would be creating today. Happy creating!<br>
<img src="./images/9.png" alt="drawing" width="300"/><br>
## Simulating your circuit
Now look to your top right. You can see this toolbar over here.<br>
<img src="./images/4.png" alt="drawing" width="300"/><br>
You would see a plethora of blocks that you can code from. We would look into text-base coding later. But now, let's go through the block-base coding. If you have used scratch before, this process of coding will seem pretty familiar.<br>
Now it's time for us to code! Let's try to make the circuit blink for 2Hz when the button is pressed. First of all, we need a loop.<br>
<img src="./images/10.png" alt="drawing" width="300"/><img src="./images/11.png" alt="drawing" width="300"/><img src="./images/12.png" alt="drawing" width="300"/><br>
Take note that there are 3 different loops you can choose from Tinkercad. Seeing that we want the code to go forever as of now, let's choose the left most loop, the 'forever' loop. I hope that it does not require that much explanation. Next, in order to determine what the code should do when the button is pressed, we need an if statement.<br>
<img src="./images/13.png" alt="drawing" width="300"/><br>
Take note that there is also an if-else statement that you could use, but that's if you wish for the code to do something <b>else</b> when the button is not pressed. With each if statement, there must be a condition. Now drag your if statement into the loop. That would make the code run <b>forever</b>. We need the if statement to be true when the button value is equal to one. So with that, drag a compare and a 'read digital pin' block into the condition.<br>
<img src="./images/14.png" alt="drawing" width="300"/><br>
Now that you have the condition, it is time for us to create the action. We would need to turn the lights on for 500ms and the lights off for 500ms.
