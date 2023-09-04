# AWS-Deepracer
This is a group project using Reinforcement Learning for realizsing the auto-driving.

Abstract:
A DeepRacer model can be optimized by using up scaled waypoints to reward the model for maintaining a racing line, by ensuring that it has a decision space which allows high-speed as well as hairpin turns, by cloning and retraining the model, and by iterating experimentation to determine ideal hyper-parameters.

Index Terms: Amazon DeepRacer, neural networks, Huber-loss, re-training, deep learning.

Video for the final result on the track done by our car:
https://user-images.githubusercontent.com/58734009/203852944-1f798bdb-a50a-404a-8e4e-69f0ac352002.mp4


Some reward functions used in AWS Deepracer:

In the first approach, we encourage the car to stay near the centerline of the track at all times and help the car to speed up/down based on the direction of the path. It is done by:\
1) Minimize the difference between the heading of the car and the current direction of the path, shown in Figure 1 below.\
2) Add future steps to detect if there will be a corner in the future so that the car could have the ability to “foresee” the future path (Figure 2 below).

<div align="center">
<img style="overflow:hidden;" src="https://user-images.githubusercontent.com/58734009/203851484-995ea9ff-26be-462f-8cfc-3705ac347da9.jpg" width=45%>
<img style="overflow:hidden;" src="https://user-images.githubusercontent.com/58734009/203851492-e9084b7c-f39d-4e6f-8284-76789a5da725.png" width=45%>
</div>

The main drawback for this approach is that although it could help the car to adjust the speed when there is a corner, the car has to make a big steering angle when passing a sharp turn. So even if we trained for a long time, there is still a high probability for the car to be off track.

As for improvement, we made the car as the center of a circle with radius r and calculated the intersection of that circle with the centre line of the path, shown in Figure below. Then the car aims and travels at the intersection (future way-point) directly, and the path is equivalent to making a tangent line.

<div align="center">
<img style="overflow:hidden;" src="https://user-images.githubusercontent.com/58734009/203851507-19a4c2da-46b1-401c-9cdd-9f1de2fff291.png" width=45%>
</div>
  
Referred from: https://medium.com/twodigits/aws-deepracer-how-to-train-a-model-in-15-minutes-3a0dca1175fb
