# sam2合集，用于sam2微调，onnx导出，单帧推理，视频推理
## 功能
  * sam2用于点和框作为提示信息的微调
  * onnx导出
  * sam2+手动提示框分割，可生成mask标签用于自动化标注
  * sam2+yolov8自动分割，可生成mask标签用于自动化标注
  * sam2视频推理(2024/11/23日更新)

## 环境
 * sam2: pip install -e .
 * onnx: pip install onnx
 * ultralytics: pip install ultralytics

## sam2微调
 数据：将图片和mask标签放在Image文件夹与Instance下，图片名称与标签名字保持一致
![28c3c499060af1415b05bda828f4f40](https://github.com/user-attachments/assets/2fc523f5-a20d-48cf-aae5-9da009cafc8c)
![3b894b8009217f72e6383f89938455e](https://github.com/user-attachments/assets/ac9b088e-822c-4be7-907e-448afa483bb1)

 * 使用点作为提示信息微调[tools/train_point.py](./tools/train_point.py)
 * 使用点+框作为提示信息微调[tools/train_box.py](./tools/train_box.py)

 微调后会在[tools](./tools)文件夹下生成model.torch格式文件，加载微调权重方式参考[tools/inference.py](./tools/inference.py)中sam2_model函数。
## onnx导出
 * [export_sam2onnx.py](./tools/export_sam2onnx.py)
 
 会在[tools](./tools)文件夹下生成decoder、encoder的onnx文件。参考[ONNX-SAM2-Segment-Anything](https://github.com/ibaiGorordo/ONNX-SAM2-Segment-Anything)测试onnx格式模型导出是否成功。可使用c++推理部署[Sam2Onnx_Inference](https://github.com/lyxlplhy/Sam2Onnx_Inference)。
## sam2+手动给提示框分割，可生成mask标签
 * [inference2.py](./tools/inference2.py)
## sam2+yolov8自动分割，可生成mask标签
 * [inference.py](./tools/inference.py)
## sam2视频推理
 * 代码中视频路径为视频抽帧后存放的文件夹，图片命名方式为0.jpg、1.jpg等 [inference_video.py](./tools/inference_video.py)
## 参考
* sam2: [https://github.com/facebookresearch/sam2](https://github.com/facebookresearch/sam2)
* 60行代码就可以训练/微调 Segment Anything 2 (SAM 2): [https://avoid.overfit.cn/post/9598b9b4ccc64a8e86275f1e7712e0dd](https://avoid.overfit.cn/post/9598b9b4ccc64a8e86275f1e7712e0dd)
* ultralytics: [https://github.com/ultralytics/ultralytics](https://github.com/ultralytics/ultralytics)
* ONNX-SAM2-Segment-Anything：[https://github.com/ibaiGorordo/ONNX-SAM2-Segment-Anything](https://github.com/ibaiGorordo/ONNX-SAM2-Segment-Anything)
* Sam2Onnx_Inference: [https://github.com/lyxlplhy/Sam2Onnx_Inference](https://github.com/lyxlplhy/Sam2Onnx_Inference)
   
