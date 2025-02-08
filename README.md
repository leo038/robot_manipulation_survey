# robot_manipulation_survey
Summary of work related to general robot manipulation.



## 二指夹爪抓取

主流的抓取研究一般有2类： 2D平面抓取和6-DoF抓取。 2D平面抓取时， 机械抓手垂直于物体所在的平面，只能从一个方向抓取， 这对物体的抓取有很大限制。
6-DoF抓取可以从空间任意方向进行抓取， 有很大的灵活性。 6-DoF也不严格是指有6个自由度， 而是至少有6个自由度，三维旋转和三维的抓取中心。有时可能还有夹爪的宽度等，
一般也统称6-DoF抓取， 有些文献可能叫7-DoF抓取。

这里主要总结6-DoF的抓取， 不关注2D平面抓取。 

- [GraspNet: An Efficient Convolutional Neural Network for Real-time Grasp Detection for Low-powered Devices](https://www.ijcai.org/proceedings/2018/0677.pdf)  IJCAI 2018


- [Volumetric Grasping Network: Real-time 6 DOF Grasp Detection in Clutte](https://arxiv.org/abs/2101.01132) CoRL  2020




上海交通大学团队系列工作： 

- [GraspNet-1Billion: A Large-Scale Benchmark for General Object Grasping](https://openaccess.thecvf.com/content_CVPR_2020/papers/Fang_GraspNet-1Billion_A_Large-Scale_Benchmark_for_General_Object_Grasping_CVPR_2020_paper.pdf)  CVPR 2020

  核心工作是提出了一个大型的抓取姿态检测数据集和评估系统， 包含约10万张图像和10亿个标注的抓取姿态。另外也提出了一个抓取检测网络作为基准。



-  [RGB Matters: Learning 7-DoF Grasp Poses on Monocular RGBD Images](https://arxiv.org/abs/2103.02184)  ICRA 2021
  
    核心思路是把抓取姿态估计解耦成2个问题： 通过单目RGB图像产生热力图去预测在图像上的抓取位置和夹爪的方向，然后通过热力图和深度图预测夹爪的宽度和夹爪与图像的距离。
而以往的方法一般是通过RGBD图像得到点云，忽略了RGB图像中很多丰富的信息。  这种方法降低了对深度信息的依赖， 提高了在深度信息不太准的情况下的鲁棒性。


- [Contact-GraspNet: Efficient 6-DoF Grasp Generation in Cluttered Scenes](https://arxiv.org/abs/2103.14127)  ICRA 2021


- [Graspness Discovery in Clutters for Fast and Accurate Grasp Detection](https://arxiv.org/abs/2406.11142)  ICCV 2021
    
    核心工作是提出了抓取质量度量-graspness， 预过滤掉了大多数低质量的抓取姿态， 极大地提高了效率和精度。 该工作已被集成到AnyGrasp中， 但未开源代码， 仅提供动态链接库供调用。

- [TransCG: A Large-Scale Real-World Dataset for Transparent Object Depth Completion and a Grasping Baseline](https://arxiv.org/abs/2202.08471) 2022

    主要解决透明物体的抓取。 


 
-  [AnyGrasp: Robust and Efficient Grasp Perception in Spatial and Temporal Domains](https://graspnet.net/anygrasp)   T-RO 2023
    
    主要贡献是考虑了动态物体的抓取。

  Graspnet-1 Billion解读: [https://zhuanlan.zhihu.com/p/703428650](https://zhuanlan.zhihu.com/p/703428650)


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


上海交通大学 [GraspNet-1Billion](https://graspnet.net/) 2020

google: [Open X-Embodiment](https://robotics-transformer-x.github.io/)   2023


斯坦福 [Mobile ALOHA](https://mobile-aloha.github.io/)   (这不是一个具体的数据， 而是一套机器人数据采集系统)     2024


智元： [AgiBot-World](https://agibot-world.com/)   2025




**数据集的区别:**

GraspNet-1 Billion 主要专注于 抓取姿态检测 和 机器人视觉与操作，适用于需要大量抓取姿态数据的研究和应用。 

Agibot World 则涵盖了 更广泛的任务类型，包括家庭、餐饮、工业、商超和办公场景中的多样化技能，适用于需要机器人在复杂环境中执行多种任务的应用。



## 参考链接
[近年来机器人主流抓取估计方法总结](https://blog.51cto.com/u_14411234/3094747)

[机器人抓取汇总|涉及目标检测、分割、姿态识别、抓取点检测、路径规划](https://cloud.tencent.com/developer/inventory/1112/article/1587723)

[学习报告：机器人抓取中物体定位、位姿估计和抓取估计算法综述](https://www.scholat.com/teamwork/showPostMessage.html?id=10653)