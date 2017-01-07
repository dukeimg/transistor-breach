# transistor-breach
А small unitily that will help you to listen and record .bank of Transistor or any other game.

*For educational purposes only*

## Usage

Steps to set up:

1. Get and install the FMOD Studio Programmer’s API and Low Level Programmer API
2. Install it. On linux copy the files in the zip you get above from `/api/*/lib/x86_64/*` to `/usr/local/lib`, run 

   `$ sudo ldconfig` 
   
   then 
   
   `$ export LD_LIBRARY_PATH=/usr/local/lib`
   
   Optional: run `$ export` to make sure that 
   
   `declare -x LD_LIBRARY_PATH="/usr/local/lib"` presists.

3. Adjust two things in the source code: 
  1. First, change 
  
    `ERRCHECK(lowLevelSystem->setPluginPath("/home/matthew/Documents/FMOD/test"));`
  
    on line 193 so that the `dll/so/dylib` named `FModPlugins` (which is found in the transistor install directory under `lib64`) can be found at the path written. 
  2. Second, adjust `SOUND_DIR` at the top of the file to where the file MasterBank.bank can be found on your hard drive (It’s in the transistor installation directory, just modify mine so it fits yours).
  
4. Compile source with the following command: 

 `g++ fmod-breach.cpp -m64 -o test -I/PATHTOFMODZIP/api/studio/inc -I/PATHTOFMODZIP/api/lowlevel/inc -lfmodstudio -lfmod -lpthread`
   
   You should also be able to do this in visual studio fairly easily. Just make sure you add the libraries to the project properties.
   
5. Run the resultant exe!

## ToDo:

- [ ] Fix the Issue #1. Teach `FMOD_OUTPUTTYPE_WAVWRITER` to break looped events, so it can write file without memory leaking.
- [ ] Make a user-friendly tool that works with any videogame that has .bank files.

## Credits

Great thanks to Steven La (@[stevenla](https://github.com/stevenla "Steven La")) for inspiration and Matthew Ready and his [blog](https://craxic.com/transistor-sound-ripper/ "Transistor Sound Ripper") for giving me the actual working example. 

No files of Transistor are used in this repository. Respect other people's rights. If you're looking just for the music, buy an [official soundtrack](https://supergiantgames.bandcamp.com/album/transistor-original-soundtrack "Transistor Oficial Soundtrack") 

## P.S.

*If someone founds this repository, feel free to contribute here. You can totaly make a .bank sounds unpacking tool out of this draft. Unfortunately, as a Ruby developer who knows nothing about C++, I don't have that much time to make it by myself.*

