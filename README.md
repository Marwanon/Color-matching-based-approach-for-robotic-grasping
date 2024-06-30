# Color-matching-based-approach-for-robotic-grasping

## Summary:
Object grasping is a basic but difficult task in robotic manipulation due to various object size, shapes and other properties. The problem becomes more challenging when the robot has to reach for and grasp a particular object in cluttered environments. To this end, the color of object can be one of the important features for identifying the target object to be picked up. In this paper, we investigate an approach of training a robot so that it is able to locate the target object by matching its color, and goes on to pick up the object in an unsupervised learning manner. The proposed approach is divided into two parts: 1) a semantic segmentation module that locates the target object by segmenting the color image and creates a mask on the predicted target object, 2) an object pose estimation module that predicts the optimal grasp position of target object based on a deep reinforcement learning framework. The proposed approach was evaluated with various testing scenarios of handling single and multiple colored target objects. The experimental simulation results indicate that the suggested approach achieves an overall success rate of 92% in the grasping task.
![Proposed Approach](images/Picture1.png)

Some manufacturing tasks, on the other hand, entail the grasping of a certain object but not all objects. In such a situation, the most efficient and easy way is to infer the target object by detecting the object's color feature. To accomplish this, we suggest a color matching approach for grasping that predicts the target object based on its color. Figure. I illustrates an example depicting the scene that is used in our robot grasp detection strategy.
![reason behind this approach](images/Picture2.png)

Here we have test our approach based on two scenarios as:
![Proposed Approach](images/Picture3.png)

## Dependencies
```
- Ubuntu 20.04 or it can be run on CPU
- Python 3
- PyTorch 0.4
```
We use [CoppeliaSim 4.1][5] as the simulation environment.

## Code
We do experiments on a NVIDIA Geforce RTX (4 gp). it can be run on cpu or gpu.

First run CoppeliaSim and open the file ```simulation/simulation.ttt``` to start the simulation. Then download the pre-trained models by running

```
sh downloads.sh
```

### Training
To train from scratch, run

```
python main.py
```

### Testing
```
python main.py
--is_testing --test_preset_cases --test_target_seeking
--load_ckpt --critic_ckpt CRITIC-MODEL-PATH --coordinator_ckpt COORDINATOR-MODEL-PATH
--config_file TEST-CASE-PATH
```

e.g. 
python main.py --is_testing --test_preset_cases --test_target_seeking --load_ckpt --critic_ckpt pre-trained/critic.pth --coordinator_ckpt pre-trained/coordinator.pth --config_file  simulation/preset/coordination-00.txt

The files of the test cases are available in ```simulation/preset```.


## Vidoes
[Click here to watch the video](images/case1.gif)


## Acknowledgments
We use the following code in our project
- https://github.com/choicelab/grasping-invisible
- https://github.com/andyzeng/visual-pushing-grasping
- https://github.com/DrSleep/light-weight-refinenet

## Citation 
M. Q. Mohammed, L. C. Kwek, S. C. Chua and E. Ai Alandoli, "Color Matching Based Approach for Robotic Grasping," 2021 International Congress of Advanced Technology and Engineering (ICOTEN), Taiz, Yemen, 2021, pp. 1-8, doi: 10.1109/ICOTEN52080.2021.9493540.
https://ieeexplore.ieee.org/abstract/document/9493540 

V

