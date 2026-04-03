#南京多场景轨迹数据集 (Nanjing Multi-Scene Trajectory Dataset)  

1. 数据集简介 (Introduction)

	本数据集 是一个针对无信号控制路段（Unsignalized Roads）的行人过街轨迹预测构建的真实世界数据集。与传统的公开数据集（如 ETH/UCY, PIE, JAAD）相比，本数据集更聚焦于无信号控制路段这一高风险交通场景，重点关注行人在没有明确交通信号指引下，与机动车、非机动车及周围环境的复杂交互行为。

数据集主要特点：

- 真实场景：数据采集自真实的无信号控制路段（人行横道、路段中间过街等），包含丰富的动态交互（人-车交互、人-人交互）。
- 丰富的上下文信息：不仅包含行人的历史轨迹，还融合了周围车辆的运动轨迹。

2. 数据采集与处理 

- 采集设备：【 固定路侧摄像头】
- 采集地点：南京市【金沙井三山花园、秦虹路铁路桥路口路段、中华路瞻园路交叉口】的无信号控制路段。
  
  
- 视频参数：分辨率 1920x1080】，帧率 30 FPS / 降采样至 10 FPS。
    收集序号 	    时间信息    	  场景地点  	 视频总时长 
    第一次收集	2022年2月（冬季） 	中华路-瞻园路 	1740min
    第二次收集	2022年6月（夏季） 	秦虹路-铁路桥路	2484min
    第三次收集	2022年10月（秋季）	金沙井-三山花园	2992min
- 数据规模：
     数据 	不同行人连续轨迹条数（>12帧）	不同行人连续轨迹条数（>21帧）	 数据时长 
    金沙井 	      1393      	      1138      	105min
    秦虹路 	      598       	      460       	105min
    中华路 	      332       	      266       	48min 

3. 数据集目录结构

下载并解压数据集后，目录结构如下：

    datasets/
    └── ours/              
        ├── jinshajing1.txt    
        ├── jinshajing2.txt
        ├── qinhonglu1.txt
        ├── qinhonglu2.txt
        ├── zhonghualu.txt
        ├── jinshajing1/       
        │   ├── jinshajing1_.txt
        │   ├── jinshajing1__train.txt
        │   └── jinshajing1__val.txt
        ├── jinshajing2/       
        │   ├── jinshajing2_.txt
        │   ├── jinshajing2__train.txt
        │   └── jinshajing2__val.txt
        ├── qinhonglu1/        
        │   ├── qinhonglu1_.txt
        │   ├── qinhonglu1__train.txt
        │   └── qinhonglu1__val.txt
        ├── qinhonglu2/        
        │   ├── qinhonglu2_.txt
        │   ├── qinhonglu2__train.txt
        │   └── qinhonglu2__val.txt
        └── zhonghualu/        
            ├── zhonghualu_.txt
            ├── zhonghualu__train.txt
            └── zhonghualu__val.txt

4. 数据格式说明 

4.1 轨迹数据格式 

轨迹数据以 .txt) 格式提供，每行代表一个目标在特定帧的状态。字段定义如下：

  列名 (Column)	数据类型  	说明 (Description)            
  frame_id   	Int   	当前视频的帧序号                    
  agent_id   	Int   	目标的唯一追踪ID (同一个目标在不同帧ID相同)   
  agent_type 	String	目标类型 (如：Pedestrian, Vehicle)
  pos_x      	Float 	目标的 X 坐标                    
  pos_y      	Float 	目标的 Y 坐标                    

示例：

    frame_id, agent_id, agent_type, pos_x, pos_y
    0.0 1 Vehicle -28.830148 15.15304069
    0.0 2 Vehicle -28.74744027 15.22553298
    0.0 3 Pedestrian -29.47366034 14.84854927
    0.0 4 Vehicle -28.59056531 15.21347541
    0.0 5 Vehicle -28.81287137 14.65806441

6. 隐私与数据脱敏 

为了保护个人隐私，本数据集中的所有视频和图像均已进行脱敏处理。所有行人的面部特征以及车辆的车牌号码均已使用模糊算法（Blurring）进行打码。本数据仅供学术研究使用，严禁用于任何商业目的或尝试重新识别个体。

7. 引用说明 

如果您在您的研究中使用了本数据集，请引用以下论文：

    @article{zhou2023multimodal,
      title={A Multimodal Trajectory Prediction Method for Pedestrian Crossing Considering Pedestrian Motion State},
      author={Zhou, Zhuping and Liu, B. and Yuan, Changji and others},
      journal={IEEE Intelligent Transportation Systems Magazine},
      year={2023}
    }

8. 联系方式 

如有任何关于数据集的问题，请联系：

- 姓名：储小松 (Xiaosong Chu)
- 邮箱：124110023597@njust.edu.cn
- 单位：南京理工大学 

9. 许可证 

本项目遵循 Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License (CC BY-NC-SA 4.0) 协议开源。仅限非商业性学术研究使用。
