# **Whiteberry** SIBER SIAGA Writeup Sept 2025

# 

# REVERSE

## GUESS PWD

![](images_Siber%20Siaga%20Round%201%202025/0.png)  
The provided file contains a android apk file  
![](images_Siber%20Siaga%20Round%201%202025/1.png)

The tool will be using to decompile the apk is **jadx**

After decompiling, we can find the main code package in **com/siber25.c1**  
![](images_Siber%20Siaga%20Round%201%202025/2.png)

Inside **MainActivity** class contains a few point of interest like **flagImage, flagText, generateRandomPassword(), and checkPassword()**  
![](images_Siber%20Siaga%20Round%201%202025/3.png)

We can see that the password are randomized and the flags will only reveal when the password is correct.  
![](images_Siber%20Siaga%20Round%201%202025/4.png)

But we can instantly find the flag by using the **jadx built-in text search**   
![](images_Siber%20Siaga%20Round%201%202025/5.png)  
Only search definition of **Resource** is enabled![](images_Siber%20Siaga%20Round%201%202025/6.png)

We found the flag is located in **res/layout/activity\_main.xml**  
![](images_Siber%20Siaga%20Round%201%202025/7.png)  
**SIBER25{y0u\_cr4ck\_l061n\_w17h\_wh47\_w4y?}**

# BLOCKCHAIN

## Puzzle

![](images_Siber%20Siaga%20Round%201%202025/8.png)

This challenge contains a url and a file called **Puzzle.zip**

The tool involved is **Remix IDE** and **MetaMask**

We first access the provided url and are greeted with Blockchain Launcher  
![](images_Siber%20Siaga%20Round%201%202025/9.png)

We first click the **Solve in Browser** under **Challenge** and wait for it to complete.  
![](images_Siber%20Siaga%20Round%201%202025/10.png)

Once it’s done solving, a generated string appears in the Solution field  
![](images_Siber%20Siaga%20Round%201%202025/11.png)  
We then click **Submit Solution** which allows us to **Launch** instance, which generates the needed credentials to use  
![](images_Siber%20Siaga%20Round%201%202025/12.png) 

Now we head to metamask to add the the **RPC\_URL** and **PRIVKEY**  
**![](images_Siber%20Siaga%20Round%201%202025/13.png)![](images_Siber%20Siaga%20Round%201%202025/14.png)**

Now we head to Remix IDE where we will import the challenge’s zip file which contains 2 solidity files  
**![](images_Siber%20Siaga%20Round%201%202025/15.png)**

Under Deploy & Run Transactions in Remix IDE, we set the Environment to **MetaMask** and the select wallet that was provided earlier  
![](images_Siber%20Siaga%20Round%201%202025/16.png)   
Make sure the contract is set to **Setup.sol**  
Then we copy the **SETUP\_CONTRACT\_ADDR**  from the site that gave the credentials and enter it in **At Address** field before clicking the **At Address button**  
![](images_Siber%20Siaga%20Round%201%202025/17.png)

We now have a deployed smart contract, now need to click **getPuzzle** to get the contract address for our Puzzle.sol. Repeat the same process but with **Puzzle.sol** and the given address  
![](images_Siber%20Siaga%20Round%201%202025/18.png)![](images_Siber%20Siaga%20Round%201%202025/19.png)![](images_Siber%20Siaga%20Round%201%202025/20.png)

In Puzzle.sol, we can see a **XOR** operation  
![](images_Siber%20Siaga%20Round%201%202025/21.png)

And at the bottom there’s **seedVarStateChanging(uint8 x)** which is what we need to solve  
![](images_Siber%20Siaga%20Round%201%202025/22.png)

The condition is basically (x * x + 7) mod 256 where x have to be a value where it results to 0.

There’s probably a better way but we just scroll through a list of the first 1000 squared numbers and find which is the nearest that can be divided to 256. In this case we found **x = 53**

![](images_Siber%20Siaga%20Round%201%202025/23.png)

After clicking **seedVarStateChanging**, metamask will ask to transact and we click **confirm**![](images_Siber%20Siaga%20Round%201%202025/24.png) 

Once the Transaction is confirmed, we can click **reveal** button and receive the flag  
![](images_Siber%20Siaga%20Round%201%202025/25.png)  
**SIBER25{uNd3R5tAnD\_T0\_C0mP13t3\_Th13\_J1g54w\_pUzZ13}**

# FORENSIC

## Dumpster Diving

![](images_Siber%20Siaga%20Round%201%202025/26.png)  
![](images_Siber%20Siaga%20Round%201%202025/27.png)  
Solutions:

Since the clue was accidentally deleted the flag, it means it should be in the recycle bin.   
Lookup the image to text and got the flag.
