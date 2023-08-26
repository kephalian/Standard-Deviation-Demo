# Standard-Deviation-Demo
 A Python program made using Matplotlib widgets that demonstrates the intuitive role of Standard deviation in  a distribution 




![Screen_Shot1]('https://github.com/kephalian/Standard-Deviation-Demo/blob/main/Screenshot_20230826-151509_Pydroid%203.png')




![Screen_Shot2]("https://github.com/kephalian/Standard-Deviation-Demo/blob/main/Screenshot_20230826-151551_Pydroid%203.png")




````

import numpy as np
import matplotlib.pyplot as plt
from matplotlib.widgets import Slider

def plot_normal_distribution(ax, std_deviation):
    ax.clear()
    mean = 0
    x = np.linspace(mean - 3*max_std_deviation, mean + 3*max_std_deviation, 100)
    y = (1/(std_deviation * np.sqrt(2*np.pi))) * np.exp(-0.5*((x - mean)/std_deviation)**2)

    ax.plot(x, y, label=f'Standard Deviation = {std_deviation}')
    ax.set_title('Intuitive understanding of Standard devation\n Change values of SD with yellow slider, observe the Normal curve')
    ax.set_xlabel('x')
    ax.set_ylabel('Probability Density')
    ax.legend()

    # Customize the grid style
    ax.grid(True, linestyle='dotted', linewidth=0.5, color='gray')
    
    # Mark the x-axis with standard deviation values
    ax.set_xticks([ mean - 3 *std_deviation, mean - 2* std_deviation,   mean - std_deviation, mean, mean + std_deviation, mean + 2*std_deviation, mean + 3*std_deviation])
    ax.set_xticklabels(['-3 × SD', '-2 × SD', '-1 × SD', 'Mean', '1 × SD', '2 × SD', '3 × SD'])
    

    # Add a thick marker line at the mean
    ax.axvline(x=mean, color='blue', linewidth=1)
    ax.axvline(x=mean - 2* std_deviation, color='green', linewidth=0.4)
    ax.axvline(x=mean + 2* std_deviation, color='red', linewidth=0.4)

    plt.draw()

fig, ax = plt.subplots()
plt.subplots_adjust(bottom=0.25)  # Adjust the bottom margin for the slider

max_std_deviation = 5.0  # Set the maximum value for standard deviation
initial_std_deviation = 2.0  # Initial value for standard deviation

std_deviation_slider_ax = plt.axes([0.25, 0.1, 0.65, 0.03], facecolor='yellow')
#(0.2, 0.7, 0.2, 0.5))
#'lightgoldenrodyellow')
std_deviation_slider = Slider(std_deviation_slider_ax, 'Std Deviation', valmin=0.1, valmax=max_std_deviation, valinit=initial_std_deviation)

plot_normal_distribution(ax, initial_std_deviation)  # Initial plot

def update(val):
    std_deviation = std_deviation_slider.val
    plot_normal_distribution(ax, std_deviation)

std_deviation_slider.on_changed(update)

plt.show()
```` 
