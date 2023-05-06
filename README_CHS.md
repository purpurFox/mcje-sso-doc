# 我的世界：Java版 服务器软优化文档
### [English](https://github.com/purpurFox/mcje-sso-doc/blob/main/README.md) | 中文

###### [广告位招租]


这是一份专门为Minecraft服主们开放的Minecraft服务器“软优化”指南。**请注意：这份指南不提供硬件优化，而是提供尽可能多的软件优化！**

## 目录
[TOC]


## 给服务器选择一个操作系统
一般情况下，Windows的运行效率低于Linux
如果你非常追求高的运行效率而且不嫌麻烦，Linux是你的不二选择，前提是你有一定的Linux基础
但是如果你嫌Linux麻烦，Windows也不是不行，因为这只是优化指南其中的一条 :)

### Linux系（运行效率推荐）
- [**Ubuntu Server** （首选）](https://cn.ubuntu.com/download/server/step1)
- [openEuler （次选）](https://www.openeuler.org/zh/download)
- [Debian](https://www.debian.org/download)
- [RHEL](https://www.redhat.com/zh/technologies/linux-platforms/enterprise-linux)
- [Arch Linux](https://archlinux.org/download)
- [*完整列表*](https://zh.wikipedia.org/wiki/Linux%E5%8F%91%E8%A1%8C%E7%89%88%E5%88%97%E8%A1%A8)

如果你选择的是 Ubuntu/Debian 或是其它Debian系，那么恭喜！你可以获得进一步的优化
#### 为你的Debian系操作系统更换Linux内核
- 详细请看： https://xanmod.org

### Windows系（操作简易推荐）
- [Windows Server](https://www.microsoft.com/zh-cn/windows-server)


## 选择一种Java运行环境（建议使用JDK）

### Minecraft版本对应Java版本
1.17及以上 使用 17及以上 ， 1.16.5~1.13 使用 17~8 ， 1.12.2及以下 使用8

### 选择一种Java发行版
更换Java发行版也是优化方式的一种

- [**GraalVM** （首选）](https://www.graalvm.org/downloads) （分为“社区版”和“企业版”两种版本）
如需更稳定的优化，请使用“社区版” ；如需更激进的优化，请使用“企业版”
- [Azul Zulu （次选）](https://www.azul.com/downloads)
- [Adoptium Eclipse Temurin](https://adoptium.net/temurin/releases)
- [BellSoft Liberica JDK](https://bell-sw.com/pages/downloads)
- [Alibaba Dragonwell](https://dragonwell-jdk.io)
- [*WhichJDK?*](https://whichjdk.com)

如果你选择的是GraalVM，那么你会在以下的“Java参数”中能够激活更多的参数


## Java参数

### PurpurFox的Minecraft参数

#### 适用于 Java 17
- 适用于 **GraalVM Community** 22.3
```bash
java -Xmx8192M -Dfile.encoding=UTF-8 -XX:+UseCompressedOops -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+UseXMMForArrayCopy -XX:-DontCompileHugeMethods -XX:+PerfDisableSharedMem -XX:+DisableExplicitGC -XX:+AlwaysActAsServerClassMachine -XX:+ParallelRefProcEnabled -XX:+AlwaysPreTouch -XX:+UseNUMA -XX:+UseDynamicNumberOfGCThreads -XX:+UseFPUForSpilling -XX:+EnableJVMCI -XX:+UseJVMCICompiler -XX:+EagerJVMCI -XX:+UseFastUnorderedTimeStamps -XX:+UseCriticalJavaThreadPriority -XX:AllocatePrefetchStyle=3 -XX:ThreadPriorityPolicy=1 -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=400M -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M -XX:+UseG1GC -XX:MaxGCPauseMillis=200 -XX:G1NewSizePercent=30 -XX:G1MaxNewSizePercent=40 -XX:G1HeapRegionSize=16M -XX:G1ReservePercent=20 -XX:G1HeapWastePercent=5 -XX:G1MixedGCCountTarget=3 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=5 -XX:+UseStringDeduplication -XX:+UseAES -XX:+UseAESIntrinsics -XX:+UseFMA -XX:+UseLoopPredicate -XX:+RangeCheckElimination -XX:+EliminateLocks -XX:+DoEscapeAnalysis -XX:+UseCodeCacheFlushing -XX:+SegmentedCodeCache -XX:+UseFastJNIAccessors -XX:+OptimizeStringConcat -XX:+UseThreadPriorities -XX:+OmitStackTraceInFastThrow -XX:+TrustFinalNonStaticFields -XX:+UseInlineCaches -XX:+RewriteBytecodes -XX:+RewriteFrequentPairs -XX:+UseFastStosb -XX:+UseNewLongLShift -XX:+UseXmmI2D -XX:+UseXmmI2F -XX:+UseXmmLoadAndClearUpper -XX:+UseXmmRegToRegMoveAll -XX:InitiatingHeapOccupancyPercent=15 -XX:SurvivorRatio=32 -XX:MaxTenuringThreshold=1 -XX:G1SATBBufferEnqueueingThresholdPercent=30 -XX:G1ConcMarkStepDurationMillis=5 -XX:G1ConcRSHotCardLimit=16 -XX:G1ConcRefinementServiceIntervalMillis=150 -XX:UseAVX=3 -XX:UseSSE=4 -XX:+OptoBundling -XX:+OptoScheduling -XX:+OptimizeFill -XX:+AlwaysCompileLoopMethods -XX:+UseCharacterCompareIntrinsics -XX:+UseCopySignIntrinsic -Xlog:async -Djava.security.egd=file:/dev/urandom -Dgraal.CompilerConfiguration=community -Dgraal.SpeculativeGuardMovement=true -Dlibgraal.WriteableCodeCache=true -XX:+EnableVectorSupport -XX:+EnableVectorAggressiveReboxing -XX:+AlignVector -XX:+UseVectorCmov -XX:+UseVectorStubs --add-modules=jdk.incubator.vector -jar server.jar --nogui
```

- 适用于 **GraalVM Enterprise** 22.3
```bash
java -Xmx8192M -Dfile.encoding=UTF-8 -XX:+UseCompressedOops -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+UseXMMForArrayCopy -XX:-DontCompileHugeMethods -XX:+PerfDisableSharedMem -XX:+DisableExplicitGC -XX:+AlwaysActAsServerClassMachine -XX:+ParallelRefProcEnabled -XX:+AlwaysPreTouch -XX:+UseNUMA -XX:+UseDynamicNumberOfGCThreads -XX:+UseFPUForSpilling -XX:+EnableJVMCI -XX:+UseJVMCICompiler -XX:+EagerJVMCI -XX:+UseFastUnorderedTimeStamps -XX:+UseCriticalJavaThreadPriority -XX:AllocatePrefetchStyle=3 -XX:ThreadPriorityPolicy=1 -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=400M -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M -XX:+UseG1GC -XX:MaxGCPauseMillis=200 -XX:G1NewSizePercent=30 -XX:G1MaxNewSizePercent=40 -XX:G1HeapRegionSize=16M -XX:G1ReservePercent=20 -XX:G1HeapWastePercent=5 -XX:G1MixedGCCountTarget=3 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=5 -XX:+UseStringDeduplication -XX:+UseAES -XX:+UseAESIntrinsics -XX:+UseFMA -XX:+UseLoopPredicate -XX:+RangeCheckElimination -XX:+EliminateLocks -XX:+DoEscapeAnalysis -XX:+UseCodeCacheFlushing -XX:+SegmentedCodeCache -XX:+UseFastJNIAccessors -XX:+OptimizeStringConcat -XX:+UseThreadPriorities -XX:+OmitStackTraceInFastThrow -XX:+TrustFinalNonStaticFields -XX:+UseInlineCaches -XX:+RewriteBytecodes -XX:+RewriteFrequentPairs -XX:+UseFastStosb -XX:+UseNewLongLShift -XX:+UseXmmI2D -XX:+UseXmmI2F -XX:+UseXmmLoadAndClearUpper -XX:+UseXmmRegToRegMoveAll -XX:InitiatingHeapOccupancyPercent=15 -XX:SurvivorRatio=32 -XX:MaxTenuringThreshold=1 -XX:G1SATBBufferEnqueueingThresholdPercent=30 -XX:G1ConcMarkStepDurationMillis=5 -XX:G1ConcRSHotCardLimit=16 -XX:G1ConcRefinementServiceIntervalMillis=150 -XX:UseAVX=3 -XX:UseSSE=4 -XX:+OptoBundling -XX:+OptoScheduling -XX:+OptimizeFill -XX:+AlwaysCompileLoopMethods -XX:+UseCharacterCompareIntrinsics -XX:+UseCopySignIntrinsic -Xlog:async -Djava.security.egd=file:/dev/urandom -Dgraal.TuneInlinerExploration=1 -Dgraal.CompilerConfiguration=enterprise -Dgraal.UsePriorityInlining=true -Dgraal.Vectorization=true -Dgraal.OptDuplication=true -Dgraal.DetectInvertedLoopsAsCounted=true -Dgraal.LoopInversion=true -Dgraal.VectorizeHashes=true -Dgraal.EnterprisePartialUnroll=true -Dgraal.VectorizeSIMD=true -Dgraal.StripMineNonCountedLoops=true -Dgraal.SpeculativeGuardMovement=true -Dgraal.InfeasiblePathCorrelation=true -Dgraal.BaseTargetSpending=160 -Dgraal.OptWriteMotion=true -Dlibgraal.WriteableCodeCache=true -XX:+EnableVectorSupport -XX:+EnableVectorAggressiveReboxing -XX:+AlignVector -XX:+UseVectorCmov -XX:+UseVectorStubs --add-modules=jdk.incubator.vector -jar server.jar --nogui
```

- 适用于**非Oracle**的Java发行版
```bash
java -Xmx8192M -Dfile.encoding=UTF-8 -XX:+UseCompressedOops -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+UseXMMForArrayCopy -XX:-DontCompileHugeMethods -XX:+PerfDisableSharedMem -XX:+DisableExplicitGC -XX:+AlwaysActAsServerClassMachine -XX:+ParallelRefProcEnabled -XX:+AlwaysPreTouch -XX:+UseNUMA -XX:+UseDynamicNumberOfGCThreads -XX:+UseFPUForSpilling -XX:+EnableJVMCI -XX:+EagerJVMCI -XX:+UseFastUnorderedTimeStamps -XX:+UseCriticalJavaThreadPriority -XX:AllocatePrefetchStyle=3 -XX:ThreadPriorityPolicy=1 -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=400M -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M -XX:+UseG1GC -XX:MaxGCPauseMillis=200 -XX:G1NewSizePercent=30 -XX:G1MaxNewSizePercent=40 -XX:G1HeapRegionSize=16M -XX:G1ReservePercent=20 -XX:G1HeapWastePercent=5 -XX:G1MixedGCCountTarget=3 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=5 -XX:+UseStringDeduplication -XX:+UseAES -XX:+UseAESIntrinsics -XX:+UseFMA -XX:+UseLoopPredicate -XX:+RangeCheckElimination -XX:+EliminateLocks -XX:+DoEscapeAnalysis -XX:+UseCodeCacheFlushing -XX:+SegmentedCodeCache -XX:+UseFastJNIAccessors -XX:+OptimizeStringConcat -XX:+UseThreadPriorities -XX:+OmitStackTraceInFastThrow -XX:+TrustFinalNonStaticFields -XX:+UseInlineCaches -XX:+RewriteBytecodes -XX:+RewriteFrequentPairs -XX:+UseFastStosb -XX:+UseNewLongLShift -XX:+UseXmmI2D -XX:+UseXmmI2F -XX:+UseXmmLoadAndClearUpper -XX:+UseXmmRegToRegMoveAll -XX:InitiatingHeapOccupancyPercent=15 -XX:SurvivorRatio=32 -XX:MaxTenuringThreshold=1 -XX:G1SATBBufferEnqueueingThresholdPercent=30 -XX:G1ConcMarkStepDurationMillis=5 -XX:G1ConcRSHotCardLimit=16 -XX:G1ConcRefinementServiceIntervalMillis=150 -XX:UseAVX=3 -XX:UseSSE=4 -XX:+OptoBundling -XX:+OptoScheduling -XX:+OptimizeFill -XX:+AlwaysCompileLoopMethods -XX:+UseCharacterCompareIntrinsics -XX:+UseCopySignIntrinsic -Xlog:async -Djava.security.egd=file:/dev/urandom -XX:+EnableVectorSupport -XX:+EnableVectorAggressiveReboxing -XX:+AlignVector -XX:+UseVectorCmov -XX:+UseVectorStubs --add-modules=jdk.incubator.vector -jar server.jar --nogui
```

### 更多的参数
- [Aikar's Flags](https://docs.papermc.io/paper/aikars-flags)
- [etil's Minecraft Flags](https://github.com/etil2jz/etil-minecraft-flags)
- [brucethemoose](https://github.com/brucethemoose/Minecraft-Performance-Flags-Benchmarks)


## 选择一种Minecraft服务端
优化效果从明显到无排序

### 主流服务端
- [**Purpur** （首选）](https://purpurmc.org/downloads)
- [Pufferfish （次选）](https://pufferfish.host/downloads)
- [Paper](https://papermc.io/downloads)
- [Spigot](https://www.spigotmc.org/wiki/buildtools) （需自行构建）
- Bukkit
- [Vanilla](https://www.minecraft.net/download/server)

### 模组服务端 （需自行安装）（需自行添加优化MOD）
- [Quilt](https://quiltmc.org/en/install)
- [Fabric](https://fabricmc.net/use/installer)
- [Forge](https://files.minecraftforge.net/net/minecraftforge/forge)

### 更多服务端
- [Glowstone](https://glowstone.net/#downloads)
- [Gale](https://github.com/GaleMC/Gale)
