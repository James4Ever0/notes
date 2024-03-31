---
title: AI工具箱
created: '2024-03-31T02:55:08.032Z'
modified: '2024-03-31T14:47:50.544Z'
---

# AI工具箱

AI工具箱 (EZ-AI-Starter):
https://www.123pan.com/s/oY9eVv-IsFnh.html pwd:1111

compiled with .net and obfusticated with pyarmor

containing:

```
My-VITS
SadTalker
stable-diffusion-webui
wav2lip
RVC
```

code for decoding encrypted environment files:

```csharp
// Decompiled with JetBrains decompiler
// Type: common.PyEnvUtil
// Assembly: common, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
// MVID: F9EBC4D1-A1AC-4DC9-BFE0-2B1E74C84F97
// Assembly location: G:\works\extract-ez-ai-tool-info\EZ-AI-Starter-1.0\launcher\common.dll

using common.entity;
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.IO;
using System.Linq;
using System.Threading;

#nullable enable
namespace common
{
  public class PyEnvUtil
  {
    private static void compareZipAndReplace(string srcZip, string targetZip)
    {
      bool flag;
      if (!File.Exists(targetZip))
      {
        flag = true;
      }
      else
      {
        if (!File.Exists(srcZip))
          throw new Exception(srcZip + " not found.");
        flag = !Util.getFileHash(srcZip).Equals(Util.getFileHash(targetZip));
      }
      if (!flag)
        return;
      File.Copy(srcZip, targetZip, true);
      Util.unZip(targetZip, Path.Combine(Path.GetDirectoryName(targetZip), Path.GetFileNameWithoutExtension(targetZip)), (Action<string>) null, false, isJoin: true);
    }

    private static bool detectVCInstalled()
    {
      ProcessStartInfo startInfo = new ProcessStartInfo()
      {
        FileName = GlobalVariable.assemblyDir + "\\vswhere.exe",
        Arguments = " -latest -products * -requires Microsoft.VisualStudio.Component.VC.Tools.x86.x64 -property installationPath",
        RedirectStandardOutput = true,
        UseShellExecute = false,
        CreateNoWindow = true
      };
      if (!File.Exists(startInfo.FileName))
      {
        Console.WriteLine("error: vswhere not found!");
        return false;
      }
      Process process = Process.Start(startInfo);
      if (process == null)
        return false;
      process.WaitForExit();
      string end = ((TextReader) process.StandardOutput).ReadToEnd();
      if (end == null)
        return false;
      string[] strArray = end.Trim().Split(new string[1]
      {
        Environment.NewLine
      }, StringSplitOptions.RemoveEmptyEntries);
      return strArray != null && strArray.Length != 0 && Directory.Exists(strArray[0]);
    }

    private static bool installVC()
    {
      Console.WriteLine("Visual Studio Installer安装中...");
      string str = GlobalVariable.assemblyDir + "\\vc.vsconfig";
      ProcessStartInfo startInfo = new ProcessStartInfo()
      {
        FileName = GlobalVariable.assemblyDir + "\\vs_BuildTools.exe",
        Arguments = " --passive --norestart --config \"" + str + "\"",
        RedirectStandardOutput = true,
        UseShellExecute = false,
        CreateNoWindow = true
      };
      if (!File.Exists(str))
      {
        Console.WriteLine("error: vc.vsconfig not found!");
        return false;
      }
      if (!File.Exists(startInfo.FileName))
      {
        Console.WriteLine("error: vs_BuildTools not found!");
        return false;
      }
      Process process = Process.Start(startInfo);
      if (process != null)
      {
        process.WaitForExit();
        Thread.Sleep(10000);
        while (true)
        {
          Process[] array = ((IEnumerable<Process>) Process.GetProcessesByName("setup")).Where<Process>((Func<Process, bool>) (p => p.MainWindowTitle == "Visual Studio Installer" || p.GetMainModuleFileName().Contains("Visual Studio\\Installer"))).ToArray<Process>();
          if (array != null && array.Length != 0)
            Thread.Sleep(500);
          else
            break;
        }
        if (!PyEnvUtil.detectVCInstalled())
        {
          Console.WriteLine("Visual Studio Installer安装失败，极有可能是网络波动造成的。务必关闭梯子、加速器等软件，然后关闭本窗口后再重装环境！");
          return false;
        }
        Console.WriteLine("Visual Studio Installer安装成功！");
        return true;
      }
      Console.WriteLine("error：vs_BuildTools启动失败，请退出后重试！");
      return false;
    }

    private static bool prepareEnv()
    {
      bool flag = true;
      PyEnvUtil.compareZipAndReplace(Path.Combine(GlobalVariable.customPythonLibPath, "pdm.zip"), Path.Combine(GlobalVariable.commonPythonHome, "Lib\\site-packages\\pdm.zip"));
      PyEnvUtil.compareZipAndReplace(Path.Combine(GlobalVariable.customPythonLibPath, "pyarmor_runtime_000000.zip"), Path.Combine(GlobalVariable.commonPythonHome, "Lib\\pyarmor_runtime_000000.zip"));
      if (!PyEnvUtil.detectVCInstalled())
        flag = PyEnvUtil.installVC();
      return flag;
    }

    public static void installPythonEnvByConsole(Application app, out Process pdmInstallProcess_)
    {
      pdmInstallProcess_ = (Process) null;
      if (!PyEnvUtil.prepareEnv())
        return;
      Console.ForegroundColor = ConsoleColor.Red;
      Console.WriteLine("重要提示：如果你的windows用户名是中文或者含有特殊符号，安装环境会失败！会出现这样的错误: 'gbk' codec can't decode byte...");
      Console.WriteLine("  这时，你要修改你的用户名为英文字母，或者重新创建一个只有英文字母的管理员账户（推荐做法），使用这个用户进入系统，就能解决这个问题了！");
      Console.ResetColor();
      Process pdmInstallProcess = (Process) null;
      string pythonEnvName = app.getPythonEnvName();
      string str = Path.Combine(GlobalVariable.appEnvBasePath, pythonEnvName);
      Directory.CreateDirectory(str);
      PythonEnvInfo pythonEnvInfo = app.getPythonEnvInfo();
      string absFilePath1 = Path.Combine(GlobalVariable.envInfoDir, pythonEnvInfo.pdmEnvFilePrefix + ".lock.s");
      string absFilePath2 = Path.Combine(GlobalVariable.envInfoDir, pythonEnvInfo.pdmEnvFilePrefix + ".toml.s");
      string decryptedPdmLockFile = Path.GetTempFileName();
      string decryptedPdmPyprojectFile = Path.GetTempFileName();
      Util.writeToFile(Util.readEncryptedFileContent(absFilePath1), decryptedPdmLockFile);
      Util.writeToFile(Util.readEncryptedFileContent(absFilePath2), decryptedPdmPyprojectFile);
      string content = Path.Combine(GlobalVariable.commonPythonHome, "python.exe");
      string pythonInterpreterPathFile = Path.Combine(str, ".pdm-python");
      string absFilePath3 = pythonInterpreterPathFile;
      Util.writeToFile(content, absFilePath3);
      string pdmTempConfigFilePath = Path.GetTempFileName();
      Util.writeToFile(GlobalVariable.pdmConfigFileContent, pdmTempConfigFilePath);
      Action action = (Action) (() =>
      {
        if (File.Exists(decryptedPdmLockFile))
          File.Delete(decryptedPdmLockFile);
        if (File.Exists(decryptedPdmPyprojectFile))
          File.Delete(decryptedPdmPyprojectFile);
        if (File.Exists(pythonInterpreterPathFile))
          File.Delete(pythonInterpreterPathFile);
        if (File.Exists(pdmTempConfigFilePath))
          File.Delete(pdmTempConfigFilePath);
        if (pdmInstallProcess == null || pdmInstallProcess.HasExited)
          return;
        pdmInstallProcess.Kill();
      });
      try
      {
        ProcessStartInfo processStartInfo = new ProcessStartInfo()
        {
          FileName = Path.Combine(GlobalVariable.commonPythonHome, "python.exe"),
          Arguments = " -m pdm sync",
          CreateNoWindow = false,
          UseShellExecute = false,
          WorkingDirectory = str
        };
        processStartInfo.EnvironmentVariables["PDM_ENTRY_CHECK"] = "PDM_ENTRY_CHECK";
        processStartInfo.EnvironmentVariables["PDM_CONFIG_FILE"] = pdmTempConfigFilePath;
        processStartInfo.EnvironmentVariables["PDM_LOCKFILE"] = decryptedPdmLockFile;
        processStartInfo.EnvironmentVariables["PDM_PYPROJECT_FILE"] = decryptedPdmPyprojectFile;
        processStartInfo.EnvironmentVariables["PDM_ARIA2"] = Path.Combine(GlobalVariable.assemblyDir, "dlib");
        processStartInfo.EnvironmentVariables["PDM_DELETE_ALL_PTH"] = "111";
        pdmInstallProcess = new Process()
        {
          StartInfo = processStartInfo
        };
        pdmInstallProcess_ = pdmInstallProcess;
        pdmInstallProcess.Start();
        pdmInstallProcess.WaitForExit();
        Util.writeToFile(app.getPythonEnvInfo().version.ToString(), Path.Combine(str, "env.version"));
      }
      catch (Exception ex)
      {
        Console.WriteLine(ex.Message);
      }
      finally
      {
        action();
      }
    }

    public static Process startEnvInstallProcess(Application app)
    {
      return Process.Start(new ProcessStartInfo()
      {
        FileName = Path.Combine(GlobalVariable.assemblyDir, "envInstall.exe"),
        Arguments = app.moduleDir + "|" + GlobalVariable.userSettings[GlobalVariable.globalKey]["GPUPlatform"],
        UseShellExecute = false,
        CreateNoWindow = false
      });
    }
  }
}

```

---

悟空工具箱;
www.5kcrm.com/ai

[Video Retalking](https://www.5kcrm.com/chat/id/20) 让视频中的人物的嘴型与输入的声音同步

[OpenVoice](https://www.5kcrm.com/chat/id/19) 一种多语言即时语音克隆工具

[WebGLM](https://www.5kcrm.com/chat/id/13) 是一个百亿参数的通用语言模型（GLM），提供一种高效且低成本的网络增强问答系统。它通过将网络搜索和召回功能，集成到预训练的语言模型中，以进行实际应用的部署。 

[DragGAN](https://www.5kcrm.com/chat/id/16) 是由Max Planck研究所开发的一种新的人工智能工具，它允许用户通过几个点击和拖动来真实地修改照片。根据一篇研究文章，它提供了两个主要组成部分：基于特征的运动监督和一种革命性的点追踪技术。 

[VisualGLM](https://www.5kcrm.com/chat/id/8) 能够整合视觉和语言信息。可以用来理解图片，解析图片内容。

---

[设计师的AI工具箱](https://space.bilibili.com/290745620) UID:290745620
AI 3D建模 动作生成

---

allAI 工具箱：
https://github.com/OceanNg529/allAI
包含视频抠图

[漫画翻译软件](https://gitee.com/allAI-tools/manga-image-translator) 可以翻译不同的排版 保持文字方向 [原地址](https://github.com/zyddnys/manga-image-translator) 

[MMD 视频字幕提取翻译](https://github.com/PatchyVideo/MMDOCR-HighPerformance)

为了加速下载 作者把链接都放到了[gitee](https://gitee.com/ocean125/)上面 可以在那里找到最新的ai工具

[moondream2](https://gitee.com/ocean125/moondream-allAI) 一个强大且能在任何地方运行的小型视觉语言模型

[differential-diffusion-ui](https://gitee.com/ocean125/differentialdiffusionui-allAI) Differential Diffusion   根据文本提示修改图像，并根据指定每个区域的变化量的地图

[supir](https://gitee.com/ocean125/supir-allAI) 基于大规模扩散的高保真通用图像恢复模型，SupIR能够根据文本提示进行智能修复，提高图像修复的质量和智能程度。

[TripoSR](https://gitee.com/ocean125/triposr-allAI) 用于从单个图像快速前馈 3D 重建，由 Tripo AI 和 Stability AI   合作开发

[dust3r](https://gitee.com/ocean125/dust3r-allAI) 从任意图像集合中重建3D场景的框架

[Lobe Chat](https://gitee.com/ocean125/lobe-allAI) 一个开源的，现代设计的ChatGPT/LLMs UI/框架。   支持语音合成，多模态和可扩展 (函数调用)插件系统。

[Chatbot-Ollama](https://gitee.com/ocean125/chatbotollama-allAI) 开源聊天UI为Ollama

[remove-video-bg](https://gitee.com/ocean125/removevideobg-allAI) 视频背景删除工具

[MeloTTS](https://gitee.com/ocean125/melotts-allAI) 高质量的多语言文本到语音库   MyShell.ai。支持英语、西班牙语、法语、中文、 日语和韩语

[gligen](https://gitee.com/ocean125/gligen-allAI) 控件中使用ComfyUI的GLIGEN的直观GUI后端

[FaceFusion 2.3.0](https://gitee.com/ocean125/facefusion-allAI) 下一代换脸器和增强器

[Stable Cascade](https://gitee.com/ocean125/stablecascade-allAI) 来自StabilityAI的稳定级联

[Bark Voice Cloning](https://gitee.com/ocean125/barkvoicecloning-allAI) 上传一个干净的20秒WAV文件的声音人物，你想模仿，输入你的文本到语音提示，并点击提交！

[BRIA RMBG](https://gitee.com/ocean125/briarmbg-allAI) 由 BRIA.AI   开发的背景去除模型，在精心挑选的数据集上进行训练，可作为非商业用途的开源模型

[ComfyUI](https://gitee.com/ocean125/comfyui-allAI) 稳定扩散和稳定视频扩散 GUI

[Stable Diffusion web UI](https://gitee.com/ocean125/automatic1111-allAI) 一键启动 Stable Diffusion web UI版

[Stable Diffusion Forge](https://gitee.com/allAI-tools/stablediffusionforge) Stable Diffusion WebUI Forge 基于 Stable Diffusion WebUI (based   on Gradio) 制作开发更容易，资源管理优化，并且加速推理。

[InstantID](https://gitee.com/ocean125/instantid-allAI) 最先进的无调音方法实现 仅使用单张图像生成ID-Preserving;   支持各种下游任务。

[PhotoMaker](https://gitee.com/ocean125/photomaker-allAI) 通过堆叠ID定制逼真的人体照片嵌入

[vid2pose](https://gitee.com/ocean125/vid2pose-allAI) 视频打开 DWPose

[Moore-AnimateAnyone-Mini](https://gitee.com/ocean125/mooreanimateanyonemini-allAI) [NVIDIA ONLY] 高效实现任何人物动画 (13G VRAM + 2G model size)

[Moore-AnimateAnyone](https://gitee.com/ocean125/mooreanimateanyone-allAI) [NVIDIA GPU ONLY] 非官方实施人物动画

[IP-Adapter-FaceID](https://gitee.com/ocean125/faceid-allAI) 输入人脸图像并将其转换为任何其他图像。适配器faceid模型的演示

[StreamDiffusion](https://gitee.com/ocean125/streamdiffusion-allAI) [NVIDIA ONLY] 实时交互生成的管道级解决方案

[Fooocus](https://gitee.com/ocean125/fooocus-allAI) 迷你版 Stable Diffusion UI

[RVC](https://gitee.com/ocean125/rvc-allAI) 基于检索的语音转换

---

[老麦的工具库](https://space.bilibili.com/486989780) UID:486989780
