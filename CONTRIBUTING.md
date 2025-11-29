# 多摄像头人脸跟踪项目贡献指南

感谢你愿意为本项目贡献力量！本文档说明如何参与 Multi-Camera Face Tracker 的开发与协作流程。

## 🏁 开始之前

### 前置要求
- 已安装 Python 3.8+
- Git 版本控制工具
- 具备以下基础知识：
  - 计算机视觉（OpenCV）
  - 人脸识别（InsightFace）
  - GUI 开发（PyQt5）

### 开发环境准备

1. **Fork 仓库并克隆**
   ```bash
   git clone https://github.com/AarambhDevHub/multi-cam-face-tracker.git
   cd multi-cam-face-tracker
   ```

2. **创建虚拟环境**
    ```bash
    python -m venv .venv
    source .venv/bin/activate  # Linux/MacOS
    .venv\Scripts\activate    # Windows
    ```

3. **安装依赖**
    ```bash
    pip install -r requirements.txt
    pre-commit install
    ```

4. **分支命名规范**
    ```
    feature/[short-description]  # 新功能
    bugfix/[issue-number]       # 缺陷修复
    docs/[topic]               # 文档修改
    ```

## 🛠 开发流程
代码结构示意：
``` 
├── core/          # 业务逻辑
│   ├── face_detection.py
│   ├── camera_manager.py
│   └── ...
├── ui/            # 图形界面
├── config/        # 配置文件
├── tests/         # 单元与集成测试
└── main.py        # 入口
```

### 进行修改
1. 创建分支
   ```bash
   git checkout -b feature/your-feature-name
   ```

2. 实施改动
    - 遵循 PEP 8
    - 所有函数添加类型标注
    - 公有方法编写清晰的 docstring

3. 更新文档
    - 补充或修正文档字符串
    - 新功能请更新 README/USAGE
    - 新配置项应提供示例

## 🧑‍💻 代码规范
Python 风格：
 - 遵循 Google Python Style Guide
 - 单行最长 88 字符
 - 统一使用 f-string

### 类型标注示例
```python
def recognize_faces(
    self,
    faces: List[Face]
) -> List[Tuple[Face, Optional[KnownFace], float]]:
    """在人脸库中识别传入的人脸。

    Args:
        faces: 经过检测的人脸列表。

    Returns:
        包含以下元素的元组列表：
        - 原始人脸对象
        - 匹配到的已知人脸（或 None）
        - 置信度分数
    """
```

### 日志规范
```python
logger.debug("Processing frame %s", frame_id)  # 详细调试信息
logger.info("Camera %d started", cam_id)      # 关键事件
logger.warning("Low confidence: %.2f", score) # 潜在问题
logger.error("Failed to save screenshot")     # 可恢复错误
logger.critical("DB connection lost")         # 致命错误
```

## 🐛 问题报告
Bug 提交模板：
```markdown
**描述**
清晰说明问题现象

**复现步骤**
1. 启动应用，使用...
2. 进入...
3. 观察...

**期望行为**
应该出现什么结果

**实际行为**
当前发生了什么

**日志/截图**
如有请附上
```

## ✅ 提交前检查
- 通过现有测试或添加新的测试用例
- 运行 `pre-commit run --all-files`
- 变更覆盖率不降低（如有测试）
- 更新相关文档与示例

## 📮 提交与合并
1. 提交信息应简洁描述改动：
   ```bash
   git commit -m "Fix: adjust recognition threshold logic"
   ```
2. 推送分支并创建 Pull Request，说明变更动机、影响范围与测试结果。
3. 审核通过后合并；若有需要，请按反馈修改并重新提交。

感谢每一位贡献者的付出！
