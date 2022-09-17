---
title: ffmpeg中英文对照 ffmpeg filter reference translated
created: '2022-09-17T06:50:26.207Z'
modified: '2022-09-17T06:51:38.886Z'
---

# ffmpeg中英文对照 ffmpeg filter reference translated

[source](https://blog.csdn.net/jackuylove/article/details/104895791/)

```
对这位仁兄的博客的基础上根据最新的ffmpeg进行了补充https://www.cnblogs.com/nlsoft/p/5195172.html
Video Filters
视频滤镜
 
 ... addroi            V->V       Mark a region of interest in a video frame.
                                  在视频帧中标记感兴趣的一段
 ... alphaextract      V->N       Extract an alpha channel as a grayscale image component.
                                  从灰度级测视图中提取阿尔法α通道分量.
 ... alphamerge        VV->V      Copy the luma value of the second input into the alpha channel of the first input.
                                  使用第一个输入视频的阿尔法α通道分量,添加或替换的第二个输入视频亮度值.
... amplify                       Amplify differences between current pixel and pixels of adjacent frames in same pixel location.
                                  放大当前像素与同一像素位置相邻帧像素之间的差异
 TS. atadenoise        V->V       Apply an Adaptive Temporal Averaging Denoiser.
                                  自适应时间平均降噪功能应用在输入的视频.
 ... ass               V->V       Render ASS subtitles onto input video using the libass library.
                                  使用libass程序库给输入视频渲染ASS字幕.
 ... avgblur           V->V       Apply average blur filter.
                                  均匀模糊滤镜
 T.. bbox              V->V       Compute bounding box for each frame.
                                  视频的每一个帧上计算边界框.
 ... bilateral         V->V       Apply bilateral filter, spatial smoothing while preserving edges.
                                  双边滤波，空间平滑同时保留边缘
 ... bitplanenoise     V->V       Show and measure bit plane noise.
                                  显示和测量位平面噪声。
 ... blackdetect       V->V       Detect video intervals that are (almost) black.
                                  检测视频中完全(几乎)黑色的时间间隔.
 ... blackframe        V->V       Detect frames that are (almost) black.
                                  检测完全(几乎)黑色的帧.
 TS. blend             VV->V      Blend two video frames into each other.
                                  两个视频帧混合到另一个帧上.
 ... bm3d                         Denoise frames using Block-Matching 3D algorithm.
                                  使用块匹配3D算法去噪帧
 T.. boxblur           V->V       Blur the input.
                                  模糊处理输入视频.
 ... bwdif                        Deinterlace the input video ("bwdif" stands for "Bob Weaver Deinterlacing Filter").                         对输入视频进行去隔行处理
 ... cas                          Apply Contrast Adaptive Sharpen filter to video stream.
                                  对视频流添加对比度自适应锐化滤波器。
 ... chromahold                   Remove all color information for all colors except for certain one.
                                  除去除某一颜色外的所有颜色信息。
 
 TS. chromakey         V->V       Turns a certain color into transparency. Operates on YUV colors.
                                  在YUV颜色空间中针对一些颜色做透明处理,应用与抠图功能,比 colorkey 滤镜边界更柔和.
 ... chromashift       V->V       Shift chroma pixels horizontally and/or vertically.
                                  水平和/或垂直移动色度像素。
 ... ciescope          V->V       Display CIE color diagram with pixels overlaid onto it.
                                  显示CIE彩色图表
 T.. codecview         V->V       Visualize information about some codecs.
                                  导出一些解码器的可视化信息.
 T.. colorbalance      V->V       Adjust the color balance.
                                  修改输入帧的三原色(红、绿、蓝)信号亮度.
 T.. colorchannelmixer V->V       Adjust colors by mixing color channels.
                                  调整输入视频帧的混合颜色通道.
 TS. colorkey          V->V       Turns a certain color into transparency. Operates on RGB colors.
                                  在RGB颜色空间中针对一些颜色做透明处理,边界较为生硬.
 ... colorhold         V->V       Remove all color information for all RGB colors except for certain one.
                                  删除除特定颜色外的所有RGB颜色的所有颜色信息。
 T.. colorlevels       V->V       Adjust the color levels.
                                  调整输入视频帧的颜色信号电平.
 TS. colormatrix       V->V       Convert color matrix.
                                  转换颜色矩阵.
 ... colorspace        V->V       Convert colorspace, transfer characteristics or color primaries. Input video needs to have an even size.       转换色彩空间，转移特征或原色。输入视频需要有一个均匀的大小。=
 T.. convolution       V->V       Apply convolution filter.
                                  使用卷积3x3或5x5滤镜,适用于锐化,模糊,边缘增强,边缘检测和浮雕等处理.
 ... convolve          V->V       Apply 2D convolution of video stream in frequency domain using second stream as impulse.                          以第二流做为脉冲，在频域内对视频流进行二维卷积。
 ... copy              V->V       Copy the input video unchanged to the output.
                                  复制输入视频,原封不动输出,主要是用于测试目的.
 ... coreimage         V->V       Video filtering on GPU using Apple’s CoreImage API on OSX.
                                  使用苹果的CoreImage API在OSX上通过GPU进行视频过滤。
 ... cover_rect        V->V       Find and cover a user specified object.
                                  查找并覆盖用户指定的矩形对象.
 ..C crop              V->V       Crop the input video to given dimensions.
                                  剪切输入视频显示区域,并给于新的尺寸.
 T.. cropdetect        V->V       Auto-detect crop size.
                                  自动检测剪切大小.
 ... cue               V->V       Delay video filtering until a given wallclock timestamp.
                                  将视频滤波延迟到指定的时间戳。
 TS. curves            V->V       Adjust components curves.
                                  利用曲线功能调整颜色分量,也可以利用图象处理软件的曲线文件来处理颜色.
 ... datascope         V->V       This filter shows hexadecimal pixel values of part of video.
                                  该滤波器显示部分视频的十六进制像素值。
 TS. dctdnoiz          V->V       Denoise frames using 2D DCT.
                                  使用二维频域过滤(2D DCT)对帧进行降噪处理.
 TS. deband            V->V       Debands video, Remove banding artifacts from input video.
                                  从输入视频中移除带状伪像.
 ... deblock           V->V       Remove blocking artifacts from input video.
                                  从输入视频中移除阻塞工件。
 ... decimate          N->V       Decimate frames (post field matching filter).
                                  定期删除重复的帧(后场匹配滤镜).
 ... deconvolve        V->V       Apply 2D deconvolution of video stream in frequency domain using second stream as impulse.                          以第二流为脉冲，在频域内对视频流进行二维反褶积。
 ... dedot             V->V       Reduce cross-luminance (dot-crawl) and cross-color (rainbows) from video.
                                  减少交叉亮度(点爬行)和交叉颜色(彩虹)从视频。
 T.. deflate           V->V       Apply deflate effect.
                                  适用于紧缩效果.
 ... deflicker         V->V       Remove temporal frame luminance variations.
                                  删除时间帧亮度变化。
 ... dejudder          V->V       Remove judder produced by pullup.
                                  删除动作产生的部分颤抖.
 T.. delogo            V->V       Remove logo from input video.
                                  对指定区域做模糊处理,比如能移除输入视频中的标识.
 ... derain            V->V       Remove the rain in the input image/video by applying the derain methods based on convolutional neural networks.    采用基于卷积神经网络的去雨方法对输入图像/视频进行去雨处理。
 ... deshake           V->V       Stabilize shaky video.
                                  试图修改水平或垂直的移位,降低颤抖让视频更稳定,这个滤镜有助于减小手持相机抖动影响.
 ... despill           V->V       Remove unwanted contamination of foreground colors, caused by reflected color of greenscreen or bluescreen.        清除前景色中由绿幕或蓝幕的反射色所引起的不必要的污染。
 ... detelecine        V->V       Apply an inverse telecine pattern.
                                  适用于电视电影的精确反向操作,颜色边界有锯齿效果.
 T.. dilation          V->V       Apply dilation effect.
                                  膨胀效果应用于视频.
 T.. displace          VVV->V     Displace pixels.
                                  移走像素,需要三个视频输入流和一个视频输出流,第一个输入源,第二和第三个输入位移的映射.
 ... dnn_processing    V->V       Do image processing with deep neural networks.
                                  使用深度神经网络进行图像处理。它与另一个过滤器一起工作，将帧的像素格式转换成dnn网络所需的格式。
 T.. drawbox           V->V       Draw a colored box on the input video.
                                  输入视频图像上绘制彩色的矩形区域.
 ... drawgraph         V->V       Draw a graph using input video metadata.
                                  利用输入视频的元数据绘制图表.
 T.. drawgrid          V->V       Draw a colored grid on the input video.
                                  在输入视频上绘制彩色网格.
 T.C drawtext          V->V       Draw text on top of video frames using libfreetype library.
                                  使用 libfreetype 程序库,在顶层帧上绘制文本字符串,文本内容可从指定文件中读取.
 T.. edgedetect        V->V       Detect and draw edge.
                                  检测并绘制边缘.
 ... elbg              V->V       Apply posterize effect, using the ELBG algorithm.
                                  使用增强型LBG(ELBG)算法,用于多色调分色印效果.
 ... entropy           V->V       Measure graylevel entropy in histogram of color channels of video frames.
                                  测量视频帧颜色通道直方图中的灰度熵。
 ..C eq                V->V       Adjust brightness, contrast, gamma, and saturation.
                                  调整亮度、对比度、灰度和饱和度.
 T.. erosion           V->V       Apply erosion effect.
                                  侵蚀效果应用于视频,类似油画处理.
 ... extractplanes     V->N       Extract planes as grayscale frames.
                                  从输入视频流中提取颜色通道分量用在单独灰度视频流的帧上.
 .S. fade              V->V       Fade in/out input video.
                                  适用于输入视频的淡入/淡出效果.
 ... fftdnoiz          V->V       Denoise frames using 3D FFT (frequency domain filtering).
                                  使用3D FFT(频域滤波)去噪帧。
 ... fftfilt           V->V       Apply arbitrary expressions to pixels in frequency domain.
                                  频域内将任意表达式用于采样的像素集.
 ... field             V->V       Extract a field from the input video.
                                  使用步进算法,从输入视频里的隔行图像中提取单场.
 ... fieldhint         V->V       Create new frames by copying the top and bottom fields from surrounding frames supplied as numbers by the hint file. 通过拷贝由提示文件作为数字提供的周围帧的顶部和底部字段来创建新的帧。
 ... fieldmatch        N->V       Field matching for inverse telecine.
                                  场匹配滤镜适用于电视电影的反向操作.
 T.. fieldorder        V->V       Set the field order.
                                  改变输入视频的场顺序.
 ... fifo,afifo        V->V       Buffer input images and send them when they are requested.
                                  缓冲输入的图像并在需要时发送它们
 ... fillborders       V->V       Fill borders of the input video, without changing video stream dimensions.
                                  填充输入视频的边框，不改变视频流的大小。
 ... find_rect         V->V       Find a user specified object.
                                  寻找用户指定的矩形区域.
 ... floodfill         V->V       Flood area with values of same pixel components with another values.
 ... format            V->V       Convert the input video to one of the specified pixel formats.
                                  输入视频转换为指定的像素格式.
 ... fps               V->V       Force constant framerate.
                                  强制设定固定帧频.
 ... framepack         VV->V      Generate a frame packed stereoscopic video.
                                  生成帧叠加的立体视频.
 ... framerate         V->V       Upsamples or downsamples progressive source between specified frame rates.
                                  上采样或下采样顺序渐进的视频源之间设定指定帧频.
 T.. framestep         V->V       Select one frame every N frames.
                                  每 N 个帧中选一个帧,设置帧步.
 ... freezedetect      V->V       Detect frozen video
                                  检测不变帧
 ... freezeframes      V->V       Freeze video frames
                                  冻结视频帧
 ... frei0r            V->V       Apply a frei0r effect.
                                  使用 frei0r 滤镜.
 T.. fspp              V->V       Apply Fast Simple Post-processing filter.
                                  用于快速和简单的后处理滤镜.
 ... gblur             V->V       Apply Gaussian blur filter
                                  应用高斯模糊滤镜
 T.. geq               V->V       Apply generic equation to each pixel.
                                  利用一般表达式改变每个像素点的特征.
 T.. gradfun           V->V       Debands video quickly using gradients.
                                  利用梯度快速移除带状伪像.
 ... graphmonitor      V->V       Show various filtergraph stats
                                  监视各种图表的统计信息
 ... greyedge          V->V       A color constancy variation filter which estimates scene illumination via grey edge algorithm and corrects the scene colors accordingly.
                                  利用灰度边缘算法估计场景光照的颜色恒常性变异滤波器，并对场景颜色进行相应的校正。
 TS. haldclut          VV->V      Adjust colors using a Hald CLUT.
                                  利用哈尔德查色表调整颜色.
 .S. hflip             V->V       Horizontally flip the input video.
                                  水平翻转显示输入视频.
 T.. histeq            V->V       Apply global color histogram equalization.
                                  适用于全局颜色直方图均衡化.
 ... histogram         V->V       Compute and draw a histogram.
                                  计算并绘制颜色分布直方图.
 T.. hqdn3d            V->V       Apply a High Quality 3D Denoiser.
                                  使用高质量三维降噪滤镜.
 ... hwmap             V->V       Map hardware frames to system memory or to another 
device.                           将帧映射到系统内存或者另一个设备
 ... hwupload          V->V       Upload system memory frames to hardware surfaces.
                                  将内存中的帧上传至硬件接口
 ... hwupdoad_cuda     V->V       Upload system memory frames to a CUDA device.
                                  将内存中的帧上传至CUDA设备
 .S. hqx               V->V       Scale the input by 2, 3 or 4 using the hq*x magnification algorithm.          利用高质量放大算法缩放视频显示大小,可输入2,3或4.
 ... hstack            N->V       Stack video inputs horizontally.
                                  把若干个输入视频合并到一个水平显示的输出视频.
 T.C hue               V->V       Adjust the hue and saturation of the input video.
                                  调整输入视频的色相和饱和度.
 ... hysteresis        V->V       Grow first stream into second stream by connecting components.                       这个不太理解
 ... idet              V->V       Interlace detect Filter.
                                  检测视频的交叉类型滤镜.
 T.. il                V->V       Deinterleave or interleave fields.
                                  允许处理不交叉的隔行图像场.
 T.. inflate           V->V       Apply inflate effect.
                                  膨胀效果用于视频.
 ... interlace         V->V       Convert progressive video into interlaced.
                                  转化为分段视频用于隔行处理,颜色边界有锯齿效果.
 ... interleave        N->V       Temporally interleave video inputs.
                                  能执行时间场交叉的各种类型.
 ... kerndeint         V->V       Apply kernel deinterlacing to the input.
                                  对输入的视频进行内核反交叉处理.
 ... lagfun            V->V       Slowly update darker pixels.
                                  缓慢更新黑色像素，滤镜使短暂的闪光显得更长
 .S. lenscorrection    V->V       Rectify the image by correcting for lens distortion.
                                  矫正图像用于校正透镜畸变.
 ... lensfun           V->V       Apply lens correction via the lensfun library
                                  通过lensfun库应用镜头校正
 ... libvmaf           V->V       Obtain the VMAF (Video Multi-Method Assessment Fusion) score between two input videos.   得到两个输入视频之间的(VMAF 多方法评估视频相融合)分数。
 ... limiter           V->V       Limits the pixel components values to the specified range [min, max].                 将像素分量的值限制在指定的范围内
 ... loop              V->V       Loop video frames.
                                  循环视频帧
 ... lut1d             V->V       Apply a 1D LUT to an input video.
                                  利用已维查色表调整颜色.
 TS. lut3d             V->V       Adjust colors using a 3D LUT.
                                  利用三维查色表调整颜色.
 ... lumakey           V->V       Turn certain luma values into transparency.
                                  将某些亮度值转化为透明度
 T.. lut               V->V       Compute and apply a lookup table to the RGB/YUV input video.
                                  利用查表计算处理 RGB/YUV 格式输入的视频.
 T.. lutrgb            V->V       Compute and apply a lookup table to the RGB input video.
                                  利用查表计算处理 RGB 格式输入的视频.
 T.. lutyuv            V->V       Compute and apply a lookup table to the YUV input video.                   
                                  利用查表计算处理 YUV 格式输入的视频.
 ... maskedclamp       VV->V      Clamp the first input stream with the second input and third input stream.               用第二输入流和第三输入流固定第一输入流    
 T.. maskedmerge       VVV->V     Merge first stream with second stream using third stream as mask.                   合并前二个输入视频,掩模到第三个输入视频,透明合并三个视频.
 ... maskfun           V->V       Create mask from input video.
                                                                  
 ... mcdeint           V->V       Apply motion compensating deinterlacing.
                                  适用于运动补偿反交叉.
 ... median            V->V       Pick median pixel from certain rectangle defined by radius.                           从某个由半径定义的矩形中选择中值像素
 ... mergeplanes       N->V       Merge planes.
                                  合并多个视频流的颜色通道分量.
 ... mestimate         V->V       Estimate and export motion vectors using block matching algorithms                        使用块匹配算法估计和导出运动矢量
 T.. metadata          V->V       Manipulate video frame metadata.
                                  操作视频帧的元数据,用于调试.
 ... midequalizer                 Apply Midway Image Equalization effect using two video streams.                          用两个视频流应用中间图像均衡效果。
 ... miniterpolate     V->V       Convert the video to specified frame rate using motion interpolation.                    使用运动插值将视频转换为指定的帧率。
 ... mix               VVV->V     Mix several video input streams into one video stream.
                                  将多个视频输入流混合到一个视频流中。
 ... mpdecimate        V->V       Remove near-duplicate frames.
                                  移除近似重复的帧.
 T.. negate            V->V       Negate input video.
                                  取消输入视频的阿尔法通道分量,滤镜效果类似底片.
 ... nlmeans           V->V       Denoise frames using Non-Local Means algorithm.
                                  使用非局部均值算法对帧进行去噪。
 T.. nnedi             V->V       Apply neural network edge directed interpolation intra-only deinterlacer.
                                  使用神经网络边缘插值法进行反隔行处理,需要加权重的二进制文件.
 ... noformat          V->V       Force libavfilter not to use any of the specified pixel formats for the input to the next filter.
                                  取消指定的像素格式,用于下一个滤镜.
 TS. noise             V->V       Add noise.
                                  视频输入帧上添加噪声.
 ... null              V->V       Pass the source unchanged to the output.
                                  不改变视频源进行输出.
 ... ocv               V->V       Apply a video transform using libopencv.
                                  使用libopencv应用视频转换
 ... oscilloscope      V->V       2D Video Oscilloscope.
                                  2D视频示波器。
 T.C overlay           VV->V      Overlay a video source on top of the input.
                                  把一个视频覆盖到另一个视频上面,需要两个输入和一个输出.
 T.. owdenoise         V->V       Denoise using wavelets.
                                  利用小波降噪法进行降噪处理.
 ... pad               V->V       Pad the input video.
                                  给输入视频添加填充新的显示区域.
 ... palettegen        V->V       Find the optimal palette for a given stream.
                                  生成最佳调色板,用于给定的视频流.
 ... paletteuse        VV->V      Use a palette to downsample an input video stream.
                                  下采样输入视频流中使用调色板,适用于生成 GIF 动态图.
 ... perms             V->V       Set permissions for the output video frame.
                                  给输出视频帧设置读/写权限.
 TS. perspective       V->V       Correct the perspective of video.
                                  校正视频的透视.
 T.. phase             V->V       Phase shift fields.
                                  对隔行视频延迟单场时间,便于场序的变化.
 ... photosensitivity  V->V       Reduce various flashes in video, so to help users with epilepsy.                         减少视频中各种闪烁，
 ... pixdesctest       V->V       Test pixel format definitions.
                                  像素格式描述符测试滤镜,主要用于内部测试.
 ... pixscope          V->V       Display sample values of color channels. Mainly useful for checking color and levels.    显示颜色通道的采样值。主要用于检查颜色和水平。
 T.C pp                V->V       Filter video using libpostproc.
                                  使用 libpostproc 后处理程序库进行过滤.
 T.. pp7               V->V       Apply Postprocessing 7 filter.
                                  使用后处理滤镜7.
 ... psnr              VV->V      Calculate the PSNR between two video streams.
                                  计算两个视频流之间的峰值信噪比(PSNR).
 ... pullup            V->V       Pullup from field sequence to frames.
                                  折叠场序用于输出帧,退回到电视电影效果.
 T.. qp                V->V       Change video quantization parameters.
                                  改变视频量化参数(QP).
 ... random            V->V       Return random frames.
                                  从内部缓存刷新出视频帧的随机帧.
 ... realtime          V->V       Slow down filtering to match realtime.
                                  减慢过滤速度,接近实时效果.
 TS. removegrain       V->V       Remove grain.
                                  移除纹理,对步进视频进行降噪处理.
 T.. removelogo        V->V       Remove a TV logo based on a mask image.
                                  利用掩模图像移除电视徽标,掩模图像的大小必须与视频相同,黑色是透明.
 ... repeatfields      V->V       Hard repeat fields based on MPEG repeat field flag.
                                  根据运动图象专家组(MPEG)重复场标志,硬执行重复场.
 ... reverse           V->V       Reverse a clip.
                                  倒放一段视频片段,需要把整个片段装入内存缓冲区.
 ... rgbashift         V->V       Shift R/G/B/A pixels horizontally and/or vertically.
                                  水平或垂直移动R/G/B/A像素。
 TSC rotate            V->V       Rotate the input image.
                                  任意角度旋转视频,用弧度表示的单位.
 T.. sab               V->V       Apply shape adaptive blur.
                                  形状自适应模糊滤镜.
 ..C scale             V->V       Scale the input video size and/or convert the image format.                          
                                  缩放输入视频的尺寸并/或改变图像格式,使用libswscale库. 
 ... scale_npp         V->V       Use the NVIDIA Performance Primitives (libnpp) to perform scaling and/or pixel format conversion on CUDA video frames.
                                  使用NVIDIA Performance Primitives (libnpp)在CUDA视频帧上执行缩放和/或像素格式转换。
 
 ..C scale2ref         VV->VV     Scale the input video size and/or convert the image format to the given reference.
                                  缩放输入视频的尺寸并/或改变图像格式用于引用视频,使用libswscale库.
 ... scroll                       Scroll input video horizontally and/or vertically by constant speed.                    以恒定的速度垂直或者水平滚动输入视频
 ... select            V->N       Select video frames to pass in output.
                                  选择视频帧用于下一个滤镜.
 TS. selectivecolor    V->V       Apply CMYK adjustments to specific color ranges.
                                  利用青色,品红色,黄色和黑色(CMYK)调整特定范围的颜色.
 ... sendcmd           V->V       Send commands to filters.
                                  给滤镜发送命令,必须插入到两个视频之间,只对具有该功能的滤镜命令有效.
 ... separatefields    V->V       Split input video frames into fields.
                                  分解输入视频帧进场,产生一个新的一半高度剪辑帧.
 ... setdar            V->V       Set the frame display aspect ratio.
                                  设置视频的显示纵横比.
 ... setfield          V->V       Force field for the output video frame.
                                  改变输出视频帧的属性,不改变视频帧的数据.
 ... setpts            V->V       Set PTS for the output video frame.
                                  设置输出视频帧的显示时间戳(PTS),可以用于快放或慢放等.
 ... setsar            V->V       Set the pixel sample aspect ratio.
                                  设置像素采样纵横比.
 ... settb             V->V       Set timebase for the video output link.
                                  设置时间轴用于视频输出帧的时间戳,主要用于测试时间轴配置.
 ... showinfo          V->V       Show textual information for each video frame.
                                  显示每个视频帧的文本信息.
 T.. showpalette       V->V       Display frame palette.
                                  显示每一帧的 256 色调色板.
 T.. shuffleframes     V->V       Shuffle video frames.
                                  打乱视频帧,重新排序和/或重复视频帧.
 ... shuffleplanes     V->V       Shuffle video planes.
                                  打乱视频映射平面,重新排序和/或重复视频映射平面.
 .S. signalstats       V->V       Generate statistics from video analysis.
                                  分析视频过程中生成统计信息.
 T.. smartblur         V->V       Blur the input video without impacting the outlines.
                                  模糊处理输入视频而不影响轮廓.
 ... split             V->N       Pass on the input to N video outputs.
                                  输入的视频分配给N个相同的视频输出.
 T.C spp               V->V       Apply a simple post processing filter.
                                  简单的后处理滤镜,设置压缩品质对视频进行压缩.
 ... ssim              VV->V      Calculate the SSIM between two video streams.
                                  计算两个输入视频之间的结构相似度(SSIM).
 .S. stereo3d          V->V       Convert video stereoscopic 3D view.
                                  视频转换成具有不同立体图像格式的三维视觉视频.
 ..C streamselect      N->N       Select video streams
                                  多个输入视频流中选择一个视频流,若干个具有相同时间长度的媒体有效.
 ... subtitles         V->V       Render text subtitles onto input video using the libass library.
                                  使用 libass 程序库输入视频上绘制字幕.
 ... super2xsai        V->V       Scale the input by 2x using the Super2xSaI pixel art algorithm.
                                  利用像素艺术扩展算法把输入视频平滑放大两倍.
 T.. swaprect          V->V       Swap 2 rectangular objects in video.
                                  视频流中交换两个矩形对象.
 ... swapuv            V->V       Swap U and V components.
                                  交换 U 和 V 映射平面分量.
 .S. tblend            V->V       Blend successive frames.
                                  两个视频帧混合到另一个帧上.
 ... telecine          V->V       Apply a telecine pattern.
                                  使用电视电影模式,颜色边界有锯齿效果.
 ... thistogram        V->V       Compute and draw a color distribution histogram for the input video across time.          不仅可以显示当前的，还可以显示过去的，对比histogram
 ... thumbnail         V->V       Select the most representative frame in a given sequence of consecutive frames.
                                  在给定的连续帧序列中选择具有代表性帧.
 ... tile              V->V       Tile several successive frames together.
                                  瓦状布局若干个连续的帧,类似视频缩略图.
 ... tinterlace        V->V       Perform temporal field interlacing.
                                  使用不同的隔行模式处理每一个帧.
 .S. transpose         V->V       Transpose input video.
                                  翻转输入视频,默认垂直翻转.
 ... trim              V->V       Pick one continuous section from the input, drop the rest.
                                  从输入视频中挑选连续的组成部分,一直到结束.
 T.. unsharp           V->V       Sharpen or blur the input video.
                                  锐化或模糊处理输入视频.
 T.. uspp              V->V       Apply Ultra Simple / Slow Post-processing filter.
                                  超慢/简单的后处理滤镜,设置压缩品质对视频进行压缩.
 ... vectorscope       V->V       Video vectorscope.
                                  显示输入视频的两个颜色分量值的二维图(矢量显示).
 ... vflip             V->V       Flip the input video vertically.
                                  垂直翻转显示输入视频.
 ... vidstabdetect     V->V       Extract relative transformations,for stabilization.
                                  提取视频的相对地变化,绘制矩形图矩阵内的箭头方向来显示变化趋势.
 ... vidstabtransform  V->V       Video stabilization/deshaking.
                                  平滑/反锐化处理视频.
 T.. vignette          V->V       Make or reverse a vignette effect.
                                  生成或扭转镜头自然渐晕效果.
 ... vstack            N->V       Stack video inputs vertically.
                                  把若干个输入视频垂直放置,所有视频的像素格式和宽度必须相同.
 TS. w3fdif            V->V       Apply Martin Weston three field deinterlace.
                                  使用马丁韦斯顿三场反隔行滤镜。
 ... waveform          V->V       Video waveform monitor.
                                  视频波形监视器.
 .S. xbr               V->V       Scale the input using xBR algorithm.
                                  应用xBR算法放大输入视频,默认是放大三倍.
 TS. yadif             V->V       Deinterlace the input image.
                                  对输入图像进行反隔行处理.
 T.. zoompan           V->V       Apply Zoom & Pan effect.
                                  用于缩放和填充效果.
 ..C zscale            V->V       Apply resizing, colorspace and bit depth conversion.
                                  用于重新调整大小,改变色隙和色彩深度.
 ... allrgb            |->V       Generate all RGB colors.
                                  生成大小为 4096x4096 的包含所有 RGB 颜色表,需要大量内存.
 ... allyuv            |->V       Generate all yuv colors.
                                  生成大小为 4096x4096 的包含所有 yuv 颜色表,需要大量内存.
 ... cellauto          |->V       Create pattern generated by an elementary cellular automaton.
                                  利用初级多孔自动生成器创建一个图案,指定模式生成无数小三角形矩阵.
 ..C color             |->V       Provide an uniformly colored input.
                                  提供了一个单色输入视频源.
 ... frei0r_src        |->V       Generate a frei0r source.
                                  提供frei0r接口,frei0r是ffmpeg的子滤镜.
 ... haldclutsrc       |->V       Provide an identity Hald CLUT.
                                  给哈尔德查色表源提供单位特征.
 ... life              |->V       Create life.
                                  生成随机花纹的图案.
 ... mandelbrot        |->V       Render a Mandelbrot fractal.
                                  生成一个曼德尔勃特集合分形,逐渐放大到指定点.
 ... mptestsrc         |->V       Generate various test pattern.
                                  生成各种测试图案,静/动态小方块矩阵和圆形图案.
 ... nullsrc           |->V       Null video source, return unprocessed video frames.
                                  生成空视频源,返回未处理的空视频帧.
 ... rgbtestsrc        |->V       Generate RGB test pattern.
                                  生成 RGB 测试图案,横向红绿蓝三条图案.
 ... smptebars         |->V       Generate SMPTE color bars.
                                  生成 SMPTE 颜色条图案,像电视测试信号视频.
 ... smptehdbars       |->V       Generate SMPTE HD color bars.
                                  生成 SMPTE HD 颜色条图案.
 ... testsrc           |->V       Generate test pattern.
                                  生成测试图案.
 ... testsrc2          |->V       Generate another test pattern.
                                  生成另一个测试图案.
 ... nullsink          V->|       Do absolutely nothing with the input video.
                                  生成空视频模板,与输入视频无关.
 ... concat            N->N       Concatenate audio and video streams.
                                  连接音频和视频流.
 ... movie             |->N       Read from a movie source.
                                  从视频源读入视频.
 ... buffer            |->V       Buffer video frames, and make them accessible to the filterchain.
                                  缓冲视频帧,并用于滤镜链.
 ... buffersink        V->|       Buffer video frames, and make them available to the end of the filter graph.
                                  缓冲视频帧,并用于滤镜图的结束.
 ... fifo              V->V       Buffer input images and send them when they are requested.
                                  缓冲输入帧,若需要时.
   
```
