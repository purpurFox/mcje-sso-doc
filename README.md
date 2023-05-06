# Minecraft : Java Edition   Server Soft Optimization Documentation
### English | [中文](https://github.com/purpurFox/mcje-sso-doc/blob/main/README_CHS.md)

###### *This is an English translation of the original Chinese page*


This is a Minecraft server "soft optimization" guide for Minecraft server owners. **PLEASE NOTE: This guide DOES NOT provide hardware optimization, but provides as many software optimizations as possible!**

## Table of Contents
[TOC]


## Choose an Operating System for the server
In general, Windows runs less efficiently than Linux
If you are very pursuing high operating efficiency and don't bother, Linux is your best choice, provided you have a certain Linux foundation
But if you think Linux is troublesome, Windows is not bad, because this is just one of the optimization guidelines :)

### Linux OS (recommended for operating efficiency)
- [**Ubuntu Server** (preferred)](https://ubuntu.com/download/server)
- [openEuler (second choice)](https://www.openeuler.org/en/download)
- [Debian](https://www.debian.org/download)
- [RHEL](https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux)
- [Arch Linux](https://archlinux.org/download)
- [*FULL LIST*](https://en.wikipedia.org/wiki/List_of_Linux_distributions)

If you choose Ubuntu/Debian or other Debian-based, congratulations! You can get further optimization
#### Replace the Linux kernel for your Debian-based Operating System
- For details, please see: https://xanmod.org

### Windows OS (recommended for easy operation)
- [Windows Server](https://www.microsoft.com/en-gb/windows-server)


## Choose a Java Runtime Environment (JDK is recommended)

### The Minecraft version corresponds to the Java version
1.17 and above use 17 and above, 1.16.5-1.13 use 17-8, 1.12.2 and below use 8

### Choose a Java distribution
Replacing the Java distribution is also a way of optimization

- [**GraalVM** (preferred)](https://www.graalvm.org/downloads) (Divided into two versions: "Community Edition" and "Enterprise Edition")
For more stable optimization, please use the "Community Edition" ; For more aggressive optimization, please use the "Enterprise Edition"
- [Azul Zulu (second choice)](https://www.azul.com/downloads)
- [Adoptium Eclipse Temurin](https://adoptium.net/temurin/releases)
- [BellSoft Liberica JDK](https://bell-sw.com/pages/downloads)
- [Alibaba Dragonwell](https://dragonwell-jdk.io)
- [*WhichJDK?*](https://whichjdk.com)

If you choose GraalVM, then you will be able to activate more parameters in the following "Java Parameters"


## Java Parameters

### PurpurFox's Minecraft Flags

#### For Java 17
- For **GraalVM Community** 22.3
```bash
java -Xmx8192M -Dfile.encoding=UTF-8 -XX:+UseCompressedOops -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+UseXMMForArrayCopy -XX:-DontCompileHugeMethods -XX:+PerfDisableSharedMem -XX:+DisableExplicitGC -XX:+AlwaysActAsServerClassMachine -XX:+ParallelRefProcEnabled -XX:+AlwaysPreTouch -XX:+UseNUMA -XX:+UseDynamicNumberOfGCThreads -XX:+UseFPUForSpilling -XX:+EnableJVMCI -XX:+UseJVMCICompiler -XX:+EagerJVMCI -XX:+UseFastUnorderedTimeStamps -XX:+UseCriticalJavaThreadPriority -XX:AllocatePrefetchStyle=3 -XX:ThreadPriorityPolicy=1 -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=400M -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M -XX:+UseG1GC -XX:MaxGCPauseMillis=200 -XX:G1NewSizePercent=30 -XX:G1MaxNewSizePercent=40 -XX:G1HeapRegionSize=16M -XX:G1ReservePercent=20 -XX:G1HeapWastePercent=5 -XX:G1MixedGCCountTarget=3 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=5 -XX:+UseStringDeduplication -XX:+UseAES -XX:+UseAESIntrinsics -XX:+UseFMA -XX:+UseLoopPredicate -XX:+RangeCheckElimination -XX:+EliminateLocks -XX:+DoEscapeAnalysis -XX:+UseCodeCacheFlushing -XX:+SegmentedCodeCache -XX:+UseFastJNIAccessors -XX:+OptimizeStringConcat -XX:+UseThreadPriorities -XX:+OmitStackTraceInFastThrow -XX:+TrustFinalNonStaticFields -XX:+UseInlineCaches -XX:+RewriteBytecodes -XX:+RewriteFrequentPairs -XX:+UseFastStosb -XX:+UseNewLongLShift -XX:+UseXmmI2D -XX:+UseXmmI2F -XX:+UseXmmLoadAndClearUpper -XX:+UseXmmRegToRegMoveAll -XX:InitiatingHeapOccupancyPercent=15 -XX:SurvivorRatio=32 -XX:MaxTenuringThreshold=1 -XX:G1SATBBufferEnqueueingThresholdPercent=30 -XX:G1ConcMarkStepDurationMillis=5 -XX:G1ConcRSHotCardLimit=16 -XX:G1ConcRefinementServiceIntervalMillis=150 -XX:UseAVX=3 -XX:UseSSE=4 -XX:+OptoBundling -XX:+OptoScheduling -XX:+OptimizeFill -XX:+AlwaysCompileLoopMethods -XX:+UseCharacterCompareIntrinsics -XX:+UseCopySignIntrinsic -Xlog:async -Djava.security.egd=file:/dev/urandom -Dgraal.CompilerConfiguration=community -Dgraal.SpeculativeGuardMovement=true -Dlibgraal.WriteableCodeCache=true -XX:+EnableVectorSupport -XX:+EnableVectorAggressiveReboxing -XX:+AlignVector -XX:+UseVectorCmov -XX:+UseVectorStubs --add-modules=jdk.incubator.vector -jar server.jar --nogui
```

- For **GraalVM Enterprise** 22.3
```bash
java -Xmx8192M -Dfile.encoding=UTF-8 -XX:+UseCompressedOops -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+UseXMMForArrayCopy -XX:-DontCompileHugeMethods -XX:+PerfDisableSharedMem -XX:+DisableExplicitGC -XX:+AlwaysActAsServerClassMachine -XX:+ParallelRefProcEnabled -XX:+AlwaysPreTouch -XX:+UseNUMA -XX:+UseDynamicNumberOfGCThreads -XX:+UseFPUForSpilling -XX:+EnableJVMCI -XX:+UseJVMCICompiler -XX:+EagerJVMCI -XX:+UseFastUnorderedTimeStamps -XX:+UseCriticalJavaThreadPriority -XX:AllocatePrefetchStyle=3 -XX:ThreadPriorityPolicy=1 -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=400M -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M -XX:+UseG1GC -XX:MaxGCPauseMillis=200 -XX:G1NewSizePercent=30 -XX:G1MaxNewSizePercent=40 -XX:G1HeapRegionSize=16M -XX:G1ReservePercent=20 -XX:G1HeapWastePercent=5 -XX:G1MixedGCCountTarget=3 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=5 -XX:+UseStringDeduplication -XX:+UseAES -XX:+UseAESIntrinsics -XX:+UseFMA -XX:+UseLoopPredicate -XX:+RangeCheckElimination -XX:+EliminateLocks -XX:+DoEscapeAnalysis -XX:+UseCodeCacheFlushing -XX:+SegmentedCodeCache -XX:+UseFastJNIAccessors -XX:+OptimizeStringConcat -XX:+UseThreadPriorities -XX:+OmitStackTraceInFastThrow -XX:+TrustFinalNonStaticFields -XX:+UseInlineCaches -XX:+RewriteBytecodes -XX:+RewriteFrequentPairs -XX:+UseFastStosb -XX:+UseNewLongLShift -XX:+UseXmmI2D -XX:+UseXmmI2F -XX:+UseXmmLoadAndClearUpper -XX:+UseXmmRegToRegMoveAll -XX:InitiatingHeapOccupancyPercent=15 -XX:SurvivorRatio=32 -XX:MaxTenuringThreshold=1 -XX:G1SATBBufferEnqueueingThresholdPercent=30 -XX:G1ConcMarkStepDurationMillis=5 -XX:G1ConcRSHotCardLimit=16 -XX:G1ConcRefinementServiceIntervalMillis=150 -XX:UseAVX=3 -XX:UseSSE=4 -XX:+OptoBundling -XX:+OptoScheduling -XX:+OptimizeFill -XX:+AlwaysCompileLoopMethods -XX:+UseCharacterCompareIntrinsics -XX:+UseCopySignIntrinsic -Xlog:async -Djava.security.egd=file:/dev/urandom -Dgraal.TuneInlinerExploration=1 -Dgraal.CompilerConfiguration=enterprise -Dgraal.UsePriorityInlining=true -Dgraal.Vectorization=true -Dgraal.OptDuplication=true -Dgraal.DetectInvertedLoopsAsCounted=true -Dgraal.LoopInversion=true -Dgraal.VectorizeHashes=true -Dgraal.EnterprisePartialUnroll=true -Dgraal.VectorizeSIMD=true -Dgraal.StripMineNonCountedLoops=true -Dgraal.SpeculativeGuardMovement=true -Dgraal.InfeasiblePathCorrelation=true -Dgraal.BaseTargetSpending=160 -Dgraal.OptWriteMotion=true -Dlibgraal.WriteableCodeCache=true -XX:+EnableVectorSupport -XX:+EnableVectorAggressiveReboxing -XX:+AlignVector -XX:+UseVectorCmov -XX:+UseVectorStubs --add-modules=jdk.incubator.vector -jar server.jar --nogui
```

- For **non-Oracle** Java distributions
```bash
java -Xmx8192M -Dfile.encoding=UTF-8 -XX:+UseCompressedOops -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+UseXMMForArrayCopy -XX:-DontCompileHugeMethods -XX:+PerfDisableSharedMem -XX:+DisableExplicitGC -XX:+AlwaysActAsServerClassMachine -XX:+ParallelRefProcEnabled -XX:+AlwaysPreTouch -XX:+UseNUMA -XX:+UseDynamicNumberOfGCThreads -XX:+UseFPUForSpilling -XX:+EnableJVMCI -XX:+EagerJVMCI -XX:+UseFastUnorderedTimeStamps -XX:+UseCriticalJavaThreadPriority -XX:AllocatePrefetchStyle=3 -XX:ThreadPriorityPolicy=1 -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=400M -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M -XX:+UseG1GC -XX:MaxGCPauseMillis=200 -XX:G1NewSizePercent=30 -XX:G1MaxNewSizePercent=40 -XX:G1HeapRegionSize=16M -XX:G1ReservePercent=20 -XX:G1HeapWastePercent=5 -XX:G1MixedGCCountTarget=3 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=5 -XX:+UseStringDeduplication -XX:+UseAES -XX:+UseAESIntrinsics -XX:+UseFMA -XX:+UseLoopPredicate -XX:+RangeCheckElimination -XX:+EliminateLocks -XX:+DoEscapeAnalysis -XX:+UseCodeCacheFlushing -XX:+SegmentedCodeCache -XX:+UseFastJNIAccessors -XX:+OptimizeStringConcat -XX:+UseThreadPriorities -XX:+OmitStackTraceInFastThrow -XX:+TrustFinalNonStaticFields -XX:+UseInlineCaches -XX:+RewriteBytecodes -XX:+RewriteFrequentPairs -XX:+UseFastStosb -XX:+UseNewLongLShift -XX:+UseXmmI2D -XX:+UseXmmI2F -XX:+UseXmmLoadAndClearUpper -XX:+UseXmmRegToRegMoveAll -XX:InitiatingHeapOccupancyPercent=15 -XX:SurvivorRatio=32 -XX:MaxTenuringThreshold=1 -XX:G1SATBBufferEnqueueingThresholdPercent=30 -XX:G1ConcMarkStepDurationMillis=5 -XX:G1ConcRSHotCardLimit=16 -XX:G1ConcRefinementServiceIntervalMillis=150 -XX:UseAVX=3 -XX:UseSSE=4 -XX:+OptoBundling -XX:+OptoScheduling -XX:+OptimizeFill -XX:+AlwaysCompileLoopMethods -XX:+UseCharacterCompareIntrinsics -XX:+UseCopySignIntrinsic -Xlog:async -Djava.security.egd=file:/dev/urandom -XX:+EnableVectorSupport -XX:+EnableVectorAggressiveReboxing -XX:+AlignVector -XX:+UseVectorCmov -XX:+UseVectorStubs --add-modules=jdk.incubator.vector -jar server.jar --nogui
```

### More Flags
- [Aikar's Flags](https://docs.papermc.io/paper/aikars-flags)
- [etil's Minecraft Flags](https://github.com/etil2jz/etil-minecraft-flags)
- [brucethemoose](https://github.com/brucethemoose/Minecraft-Performance-Flags-Benchmarks)


## Choose a Minecraft server
Optimization effects are sorted from noticeable to none

### Mainstream Server
- [**Purpur** (preferred)](https://purpurmc.org/downloads)
- [Pufferfish (second choice)](https://pufferfish.host/downloads)
- [Paper](https://papermc.io/downloads)
- [Spigot](https://www.spigotmc.org/wiki/buildtools) (need to build it by yourself)
- Bukkit
- [Vanilla](https://www.minecraft.net/download/server)

### Modded Server (need to install by yourself) (need to add optimization MOD by yourself)
- [Quilt](https://quiltmc.org/en/install)
- [Fabric](https://fabricmc.net/use/installer)
- [Forge](https://files.minecraftforge.net/net/minecraftforge/forge)

### More Server
- [Glowstone](https://glowstone.net/#downloads)
- [Gale](https://github.com/GaleMC/Gale)


## Optimize the server properties file
https://github.com/YouHaveTrouble/minecraft-optimization
