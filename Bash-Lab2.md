
# Bash-Lab2-Answers :heavy_check_mark:

#### :small_blue_diamond:1. Create a script that asks for user name then send a greeting to him.

      read -p "Please Enter Your Name: " name
      echo "Welcome on board $name."

#### :small_blue_diamond:2. Create a script called s1 that calls another script s2 where:
###### a. In s1 there is a variable called x, it's value 5

    s1 file export x=5

###### b. Try to print the value of x in s2 by two different ways.

    . s1.sh
    #source s1.sh
    echo $x

#### :small_blue_diamond:3. Create a script called mycp where:

###### a. It copies a file to another
###### b. It copies multiple files to a directory.

    if [[ $# != 0 ]]; then	
      if [[ -d $1 && -d $2 ]] ; then
        echo "directory exist and copied done"
        cp -r $@
      elif [[ -d $1 && -f $2 ]] ; then
        echo "can't copy directory to file"
      elif [[ -f $1 ]] ; then
        echo "file exist and copied done"
        cp $@
      else 
        echo "Not Exist"
      fi
    else
      echo "No argument"
    fi	

#### :small_blue_diamond:4. Create a script called mycd where:


###### a. It changed directory to the user home directory, if it is called without arguments.
###### b. Otherwise, it change directory to the given directory.

    if [[ $# = 0 ]] ; then
     cd $HOME
    else
     cd $@
    fi

#### :small_blue_diamond:5. Create a script called myls where:
###### a. It lists the current directory, if it is called without arguments.
###### b. Otherwise, it lists the given directory.

    if [[ $# = 0 ]] ;then
      ls
    else
      ls $@
    fi

#### :small_blue_diamond:6. Enhance the above script to support the following options individually:
###### a. –l: list in long format
###### b. –a: list all entries including the hiding files.
###### c. –d: if an argument is a directory, list only its name
###### d. –i: print inode number
###### e. –R: recursively list subdirectories


    if [[ $# != 0 ]] ;then
      if [[ $2 = "-l" ]] ;then
      ls -l $1
      elif [[ $2 = "-a" ]] ;then                              
      ls -a $1
      elif [[ $2 = "-d" ]] ;then
      ls -d $1
      elif [[ $2 = "-i" ]] ;then
      ls -i $1
      elif [[ $2 = "-R" ]];then
      ls -R $1
      else
        ls $@
      fi
    else
      ls $@
    fi

#### :small_blue_diamond:7. Create a script called mytest where:
###### a. It check the type of the given argument (file/directory)
###### b. It check the permissions of the given argument (read/write/execute)

      if [[ -f $1 ]]; then
      echo "this is a file "
      else [[ -d $1 ]]
          echo "this is a folder" 
      fi

      if [[ -r $1 ]]; then
          echo "it is readable"
      else 
          echo "this is not readable" 

      fi
      if [[ -w $1 ]]; then  
          echo "it is writable"
      else
          echo "it is not writable"
      fi

      if [[ -x $1 ]]; then
          echo "it is executable"
      else
          echo "it is not executable"
      fi

#### :small_blue_diamond:8. Create a script called myinfo where:
###### a. It asks the user about his/her logname.
###### b. It print full info about files and directories in his/her home directory
###### c. Copy his/her files and directories as much as you can in /tmp directory.
###### d. Gets his current processes status.


    read -p "Please Enter Your Long Name: " name
    ls -l /home/$name 
    cp -r /home/$name /tmp/asCoped
    ps -u $name











