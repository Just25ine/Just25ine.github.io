# For and While Loops:

For and while loops are very important tools, as are if, elif and else statements, so here is an example containing each. Essentially, I wished to create a system that would randomly generate a chosen number of dice rolls and display the frequency that each dice face value appeared. The function of this system was a learning tool to help visualize that as the number of rolls (num_rolls) increases, the data more closely resembles what we would expect from a fair dice. Or more generally, as your sample size increases, your data approximates reality more closely and is less likely to be due to random chance.


```python
import numpy as np
import matplotlib.pyplot as plt
```


```python
dice = [1, 2, 3, 4, 5, 6]
rolls = []
num_rolls = 30

while len(rolls) < num_rolls:
	rolls.append(np.random.randint(1,7))

plt.hist(rolls, bins=6)
plt.ylabel('Frequency of Value Rolled')
plt.xlabel('Dice Values')
plt.title('Histogram Displaying the Frequency of Each Dice Face Value')
plt.xticks([1, 2, 3, 4, 5, 6], [1, 2, 3, 4, 5, 6])
plt.show

for value in dice:
	print('Frequency of Dice Face Value ' + str(value) + ':')
	frq_value = (rolls.count(value)/num_rolls)*100
	print(str(round(frq_value, 1)) + '%')
	if frq_value >= 16 and frq_value <= 17:
		print('- Approximates Expected Very Well')
	elif frq_value >= 14 and frq_value <= 19:
		print('- Approximates Expected Well')
	else:
		print('- Approximates Expected Poorly')
	print(' ')

```

    Frequency of Dice Face Value 1:
    10.0%
    - Approximates Expected Poorly
     
    Frequency of Dice Face Value 2:
    16.7%
    - Approximates Expected Very Well
     
    Frequency of Dice Face Value 3:
    10.0%
    - Approximates Expected Poorly
     
    Frequency of Dice Face Value 4:
    23.3%
    - Approximates Expected Poorly
     
    Frequency of Dice Face Value 5:
    26.7%
    - Approximates Expected Poorly
     
    Frequency of Dice Face Value 6:
    13.3%
    - Approximates Expected Poorly
     





    
![png](For-and-While-Loop-Example_files/For-and-While-Loop-Example_3_1.png)
    


