# robot_manipulation_survey
Summary of work related to general robot manipulation.



## 二指夹爪抓取

主流的抓取研究一般有2类： 2D平面抓取和6-DoF抓取。 2D平面抓取时， 机械抓手垂直于物体所在的平面，只能从一个方向抓取， 这对物体的抓取有很大限制。
6-DoF抓取可以从空间任意方向进行抓取， 有很大的灵活性。 6-DoF也不严格是指有6个自由度， 而是至少有6个自由度，三维旋转和三维的抓取中心。有时可能还有夹爪的宽度等，
一般也统称6-DoF抓取， 有些文献可能叫7-DoF抓取。

这里主要总结6-DoF的抓取， 不关注2D平面抓取。 


- [Grasp Pose Detection in Point Clouds](https://arxiv.org/abs/1706.09911)  IJRR 2017  东北大学(美国)


- [GraspNet: An Efficient Convolutional Neural Network for Real-time Grasp Detection for Low-powered Devices](https://www.ijcai.org/proceedings/2018/0677.pdf)  IJCAI 2018  IBM Research


- [Volumetric Grasping Network: Real-time 6 DOF Grasp Detection in Clutte](https://arxiv.org/abs/2101.01132) CoRL  2020    苏黎世联邦理工学院




上海交通大学团队系列工作： 

- [GraspNet-1Billion: A Large-Scale Benchmark for General Object Grasping](https://openaccess.thecvf.com/content_CVPR_2020/papers/Fang_GraspNet-1Billion_A_Large-Scale_Benchmark_for_General_Object_Grasping_CVPR_2020_paper.pdf)  CVPR 2020

  核心工作是提出了一个大型的抓取姿态检测数据集和评估系统， 包含约10万张图像和10亿个标注的抓取姿态。另外也提出了一个抓取检测网络作为基准。 基准网络的性能不是很好，AP值只有27左右 实用价值不大。 



-  [RGB Matters: Learning 7-DoF Grasp Poses on Monocular RGBD Images](https://arxiv.org/abs/2103.02184)  ICRA 2021
  
    核心思路是把抓取姿态估计解耦成2个问题： 通过单目RGB图像产生热力图去预测在图像上的抓取位置和夹爪的方向，然后通过热力图和深度图预测夹爪的宽度和夹爪与图像的距离。
而以往的方法一般是通过RGBD图像得到点云，忽略了RGB图像中很多丰富的信息。  这种方法降低了对深度信息的依赖， 提高了在深度信息不太准的情况下的鲁棒性。 最终的效果相比GraspNet-1Billion中的基准网络有微小提升， AP值到28左右。 


- [Contact-GraspNet: Efficient 6-DoF Grasp Generation in Cluttered Scenes](https://arxiv.org/abs/2103.14127)  ICRA 2021


- [Graspness Discovery in Clutters for Fast and Accurate Grasp Detection](https://arxiv.org/abs/2406.11142)  ICCV 2021
    
    核心工作是提出了抓取质量度量-graspness， 预过滤掉了大多数低质量的抓取姿态， 极大地提高了效率和精度。 AP值大幅提升到67左右。 该工作已被集成到AnyGrasp中， 但未开源代码， 仅提供动态链接库供调用。

    非官方的代码实现： [https://github.com/rhett-chen/graspness_implementation](https://github.com/rhett-chen/graspness_implementation)


- [TransCG: A Large-Scale Real-World Dataset for Transparent Object Depth Completion and a Grasping Baseline](https://arxiv.org/abs/2202.08471) 2022

    主要解决透明物体的抓取。 


 
-  [AnyGrasp: Robust and Efficient Grasp Perception in Spatial and Temporal Domains](https://graspnet.net/anygrasp)   T-RO 2023
    
    主要贡献是考虑了动态物体的抓取。

     Graspnet-1 Billion解读: [https://zhuanlan.zhihu.com/p/703428650](https://zhuanlan.zhihu.com/p/703428650)


- [Keypoint-GraspNet: Keypoint-based 6-DoF Grasp Generation from the Monocular RGB-D input](https://arxiv.org/abs/2209.08752)  2023  佐治亚理工学院

    基于点云的抓取检测受到计算量的影响， 通常需要降低点云数量， 这会导致小物体的检测失败。 本文在直接在RGBD图像上生成抓取， 具体做法是检测图像空间夹爪关键点投影，然后使用PnP算法恢复6自由度抓取姿态


- [MonoGraspNet: 6-DoF Grasping with a Single RGB Image](https://arxiv.org/abs/2209.13036) ICRA 2023  慕尼黑工业大学

    核心是只使用RGD图像进行抓取姿态估计， 无需深度信息。 


- [Efficient Heatmap-Guided 6-Dof Grasp Detection in Cluttered Scenes](https://arxiv.org/abs/2403.18546)  2024  清华大学
    
    当前大部分的抓取研究都采用了全部观察到的点云来预测抓取姿态， 忽略了从全局语义中挖掘的指导信息， 因此限制了高质量的抓取位姿生成和实时性。 本文提出了一个以抓取热图作为引导的高效局部抓取生成器。 
    
    代码地址：[https://github.com/THU-VCLab/HGGD](https://github.com/THU-VCLab/HGGD)


- [Rethinking 6-Dof Grasp Detection: A Flexible Framework for High-Quality Grasping](https://arxiv.org/abs/2403.15054) 2024 清华大学
    
    本文试图解决6自由度机器人抓取任务中的场景级和目标导向抓取的问题。提出了一个灵活的抓取框架FlexLoG，由灵活的引导模块和本地抓取模型组成，能够同时处理场景级和目标导向抓取。



- [Efficient End-to-End 6-Dof Grasp Detection Framework for Edge Devices with Hierarchical Heatmaps and Feature Propagation](https://arxiv.org/abs/2410.22980) 2024 清华大学

    核心是高效、轻量， 可以部署到边缘设备。 

- [Task-Oriented 6-DoF Grasp Pose Detection in Clutters](https://arxiv.org/abs/2502.16976)  ICRA 2025 中山大学
  
    通常的抓取检测没有考虑面向不同任务的检测， 而人类在执行不同的任务时， 会以不同的方式抓取物体。本文主要研究了在杂乱场景下， 面向任务的6 dof抓取、



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

