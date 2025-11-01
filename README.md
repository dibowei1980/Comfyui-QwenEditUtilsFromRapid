最近在应用Qwen_edit_images模型进行产品制作，在使用ComfyUI官方提供的TextEncodeQwenImageEditPlus时遇到了烦恼：该节点无法控制人物的大小。图生图时，将指定人物放到场景中时有时很大，有时很小，比例经常不正确。
      经多方查找，发现了以下解决办法：
      使用Phr00t/Qwen-Image-Edit-Rapid-AIO 在主要位置提供的nodes_qwen.py文件替换官方同名文件后可以解决：改进的TextEncodeQwenImageEditPlus节点增加了一个可控制比例的参数，完美的解决了问题，并且兼容性很好。
      两者我进行了比较：改进节点支持4个图像输入和可配置的target_size参数，使用更高质量的lanczos缩放算法；而原节点只支持3个图像输入，使用固定的1024×1024目标尺寸和area缩放算法。
      改进节点的效果明显优于老节点。
基于此，我将该节点包装后新增此节点，在不扰乱原生节点的同时可以获取增加功能。
两个节点的名称分别添加后缀"FromRapid"。