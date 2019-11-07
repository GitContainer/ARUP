# Brief Introduction
ARUP - Another bulk Rename Utility with embedded Python interpreter
Arup is a another bulk rename utility, the point special is that it does not provide any renaming options.
Only use python scripts as renaming rules.
For this reason, this tool is for programmers or python-amateurs only.
![Main dialog](https://raw.githubusercontent.com/cdhigh/ARUP/master/res/screenshots1.png)
![traceback for debug](https://raw.githubusercontent.com/cdhigh/ARUP/master/res/screenshots2.png)

## The features:
* Has built-in python interpreter, execute a python snippet to generate a desired new filename.
* Preview the renaming result before actually renaming.
* Can undo last renamed result.
* Add the code snippets you wrote to the library for reuse later.
* Sort files according to certain rules (Can also manually adjust the order).
* Filter files according to Unix filename pattern matching rules (\*.\*, a\*.mp3, ...).
* Choose to ignore certain files.

# Development
  The utility is developed using Python / PyQt5 / peewee.    
  [github repository](https://github.com/cdhigh/ARUP)

# Python script
  ARUP execute a python function and use the result for renaming.
  The signature of user function is `def rename(arg)`.
    > argument: 'arg' is a dictionary that can access elements using attributes.
    > return: This function will be called for each file to rename. return the desired new filename! return an empty string to skip renaming the file.    
  The dictionary `arg` has elements:
  * totalNum: integer, total files number in list.
  * index: integer, index of current file to rename, from 0.
  * fileName: string, file name with extension.
  * dirName: string, directory name of current file.
  * fullPathName:  full filename, including path, file name with extension.
  * tag(): function, *ONLY for music file*, you can execute `arg.tag()` to obtain tag object for current music archive.
    the tag object has the following attrbutes:
      * tag.album         # album as string
      * tag.albumartist   # album artist as string
      * tag.artist        # artist name as string
      * tag.audio_offset  # number of bytes before audio data begins
      * tag.bitrate       # bitrate in kBits/s
      * tag.comment       # file comment as string
      * tag.composer      # composer as string 
      * tag.disc          # disc number
      * tag.disc_total    # the total number of discs
      * tag.duration      # duration of the song in seconds
      * tag.filesize      # file size in bytes
      * tag.genre         # genre as string
      * tag.samplerate    # samples per second
      * tag.title         # title of the song
      * tag.track         # track number as string
      * tag.track_total   # total number of tracks as string
      * tag.year          # year or data as string

# License
   ARUP is Licensed under the [AGPLv3](http://www.gnu.org/licenses/agpl-3.0.html) license.