Some notes on how the ffts static libs were generated for iOS

cd the_code/dublermobile/src/core/3rdparty/ffts/build
cmake .. -GXcode -DCMAKE_SYSTEM_NAME=iOS -DCMAKE_OSX_ARCHITECTURES=arm64

Open Xcode project
Select the static lib as build project
Select iPhone as build target (generic iOS device)
Menu - Product - Scheme - edit Scheme - set build config to debug
Add -fembed-bitcode to "Other C Flags" in Build Settings (for App Store)
Menu - Product - Build (should output libffts.a to a folder)
Switch to release and repeat.
(had to previously #undef __ARM_NEON__ in ffts source to get this to build)

cmake .. -GXcode -DCMAKE_SYSTEM_NAME=iOS -DCMAKE_OSX_ARCHITECTURES=x86_64
Select a simulator as target device in Xcode
Build for debug and release as before