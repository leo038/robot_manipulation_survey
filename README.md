# robot_manipulation_survey
Summary of work related to general robot manipulation.

## 灵巧手抓取

代表性工作：
北京大学王鹤课题组    https://hughw19.github.io/

- [UniDexGrasp: Universal Robotic Dexterous Grasping via Learning Diverse Proposal Generation and Goal-Conditioned Policy](https://arxiv.org/abs/2303.00938)  CVPR 2023

   提出了一个2阶段的灵巧抓取框架， 第一阶段针对物体点云输入生成若干抓取手势，从中挑选一个作为目标手势之后，第二阶段使用基于目标手势的强化学习策略来执行抓取。



- [UniDexGrasp++: Improving Dexterous Grasping Policy Learning via Geometry-aware Curriculum and Iterative Generalist-Specialist Learning](https://arxiv.org/abs/2304.00464)    ICCV 2023 

    关注不同物体不同位姿的几何差异，并利用通用策略-专家策略学习方法，极大地提升了 UniDexGrasp 的泛化能力


- [DexGraspNet: A Large-Scale Robotic Dexterous Grasp Dataset for General Objects Based on Simulation](https://arxiv.org/abs/2210.02697) ICRA 2023


- [DexGraspNet 2.0: Learning Generative Dexterous Grasping in Large-scale Synthetic Cluttered Scenes](https://arxiv.org/abs/2410.23004)  CoRL 2024


- [Task-Oriented Dexterous Grasp Synthesis via Differentiable Grasp Wrench Boundary Estimator](https://arxiv.org/abs/2309.13586) IROS 2024







## 端到端机器人操作




1 google RT系列

- [RT-1](https://robotics-transformer1.github.io/)   2022
- [RT-2](https://robotics-transformer2.github.io/)   2023
- [RT-X](https://robotics-transformer-x.github.io/)   2023



2 [Octo](https://octo-models.github.io/)    2023






3 [OpenVLA](https://openvla.github.io/)    2024



## 开源机器人框架


HuggingFace: [LeRobot](https://github.com/huggingface/lerobot)  2024


## 开源数据集

google: [Open X-Embodiment](https://robotics-transformer-x.github.io/)   2023


数据采集平台： 斯坦福 [Mobile ALOHA](https://mobile-aloha.github.io/)      2024


智元： [AgiBot-World](https://agibot-world.com/)   2025

