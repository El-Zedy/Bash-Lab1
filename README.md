

# Bash-Lab1-Answers :heavy_check_mark:
### :large_orange_diamond: Using sed utility:

#### :small_blue_diamond:1- Display the lines that contain the word “lp” in /etc/passwd file.

	 sed -n '/lp/p' /etc/passwd 
   
        :arrow_up_down:
   
	 grep 'lp' /etc/passwd

#### :small_blue_diamond:2- Display /etc/passwd file except the third line.

	 sed  -n '3!p' /etc/passwd 
   
        :arrow_up_down:
   
	 sed '3d' /etc/passwd

#### :small_blue_diamond:3- Display /etc/passwd file except the last line.

	 sed '$d' /etc/passwd

#### :small_blue_diamond:4- Display /etc/passwd file except the lines that contain the word “lp”.

	 sed '/lp/d' /etc/passwd

#### :small_blue_diamond:5- Substitute all the words that contain “lp” with “mylp” in /etc/passwd file.

	 sed -n 's/lp/mylp/gp' /etc/passwd


### ::large_orange_diamond: Using awk utility: 

#### :small_blue_diamond:1- Print full name (comment) of all users in the system.

	 awk -F : '{print NR,$5}' /etc/passwd
	
  :arrow_up_down:
  
	awk '
	BEGIN{FS=":"} 
	{
		print NR,$5
	}
	END{} ' /etc/passwd


#### :small_blue_diamond:2- Print login, full name (comment) and home directory of all users.( Print each line preceded by a line number)

	 awk -F : '{print NR,$1,$5,$6}' /etc/passwd
	
  :arrow_up_down:
  
	awk '
	BEGIN{FS=":"}
	{
   	 print NR,$1,$5,$6
	} 
	END{} ' /etc/passwd
	
#### :small_blue_diamond:3- Print login, uid and full name (comment) of those uid is greater than 500

     awk '
     BEGIN{FS=":"}
       {
          if($3>500)
          {
            print NR, $1, $3, $5
          }
       } 
     END{}  ' /etc/passwd 

#### :small_blue_diamond:4- Print login, uid and full name (comment) of those uid is exactly 500

     awk '
     BEGIN{FS=":"}
      {
          if($3==500)
          {
            print NR, $1, $3, $5
          }
      } 
     END{}  ' /etc/passwd 

#### :small_blue_diamond:5- Print line from 5 to 15 from /etc/passwd

     awk '
     BEGIN{FS=":"}
      {
          if(NR>=5 && NR<=15)
          {
            print NR,$0
          }
      }
     END{} ' /etc/passwd

#### :small_blue_diamond:6- Change lp to mylp

     awk '
     BEGIN{FS=":"}
      {
          i=1
          line=""
          while(i<=NF)
          { 
            if($i == "lp"){ 
            $i="mylp";
            line=$0
          }
              i++; 
          }
          if(line != "")
          {
            print line
          }
      } 
     END{} ' /etc/passwd 

#### :small_blue_diamond:7- Print all information about greatest uid.

	 awk '
	 BEGIN{FS=":"; greatest_id=-1;greatest_row=0}
	  {
      if($3>greatest_id)
      {
        greatest_id=$3	
        greatest_row=$0
      }
	  } 
	 END{print"The greatest uid is = " greatest_id,",and its information = " greatest_row}' /etc/passwd
	

#### :small_blue_diamond:8- Get the sum of all accounts id’s.

	  awk '
	  BEGIN{FS=":"; sum=0}
	   {
		  sum=sum+$3
	   } 
	  END{print "the sum of all accounts id’s = "sum}' /etc/passwd
