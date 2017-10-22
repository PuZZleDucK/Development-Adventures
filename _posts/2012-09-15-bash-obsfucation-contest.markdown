---
layout: post
title:  "BASH Obsfucation Contest Entry"
date:   2012-09-15 19:37:56 +1100
categories: article
---

Ok, here it is at last, my XDA Developers "BASH Obsfucation Contest" entry, gee I hope Blogger doesn't chew up my formatting or escape chars... oh well here goes nothing... and let me know in the comments if you work it out :D

Here is the link to the XDA thread.
http://forum.xda-developers.com/showthread.php?p=31053651#post31053651

And another to the YouTube video.
http://www.youtube.com/watch?feature=player_detailpage&v=y-XSjjgQV80#t=151s

Checkout the script file here: http://dl.dropbox.com/u/3380589/bash%20scripts/santa.sh (the blog format exposes some of my Obsfucation... and also seems to chew up the odd character... doh, too tired to fix now).

 Spoiler alert... I tell you what it does at the end... now on with the code:


#! /bin/bash

#Init Yeuletide(sp?)
euletideness=0;                                                                                                                                                                                                                                                                                              xt="is";
merrynessindex=0;                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            lw4e="l";

#Init xMian vocab
santa="";elf="";partrige="";snowman="";jingles="";pinetrees="";
mrsclause="";elfette="";nannatriges="";noman="";bells="";tinsel="";

#init xMas graphics
#Bauble:
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         serr4="S"; # nothing to see here... move it along now
                            xt643="kes";
                          d="n";      n="d";
                       vgt=" ma";      vgr="k";
                   serr1="nt";          serr7="a ";
                 vgw="es ";                 serr8="a";
                lw9="h";         lw3="ppy";  lp23=" ..";
               lp223=".so"; vgt234=" fe";lp2333="w n";
               lp243="ice";  lp23="ren";  lp2113=" me";
                mvfd="N";ice="ice"; i="/"; lwe3="aug";
                 lw3e="hty";xa="th$xt";j="pr";m="oc";
                   vg="$vgt$vgr$vgw";ul="ev";p="mm";
                     ds="$serr4$serr8$serr1$serr7";
                        serr99="i$lw4ed";o="co";
                          lw="$lw9$serr8$lw3";

#Tree:
#######################################################################
#                                                                     #
#                             *                                       #
#                             |                                       #
#                            vg";                                     #
#                           vgt9";                                    #
#                          v8="lw9";                                  #
                         vgt58=" c$lw9";                              #
#                         3="$vgt"3r7";                               #
#                       iy223="$lw33=r7";                             #
#                     lp2223="$gt";lw=" r7";                          #
                   lp2223="$vgt";lw33=" $serr7";                      #
#                     313serr4ad"gt41=" rra";                         #
#                   lp2 3$serr4aj" vgt1="sr4a";                       #
#                lp13="$serr4ad"; vgt4321="err4a";                    #
#               2313="$serr4ad"; vgt4321=" $serr4a";                  #
               lp2313="$serr4ad"; vgt4321=" $serr4a";                 #
#                 p2323="$serr1;lp221;n2="$mvfdce";                   #
#               lp232$serr1a";l2213=".";n2=mvfd$ic";                  #
#             lp2323="$serr1ajh;221jhg"."j;n2fg="fd$ie"               #
             lp2323="$serr1a";lp2213=".";n2="$mvfd$ice";              #
#             n1="$mwe3w3;l=err8";hg="t $i";e="$l$m$i";               #
#           n1="$mvfwe3$lw3e";l=l"serr8";k=" $"e="$j$m$i";            #
#          n1="$mvd$lw3$lw3e";l="c$ser";k="t $h";e=$l$$j$i";          #
#        n1="$mvfd$lwe3$lw3e";l="c$serr8";k="t $i";e="l$k$j$i";       #
        n1="$mvfd$lwe3$lw3e";l="c$serr8";k="t $i";e="$l$k$j$m$i";     #
#          a="$i$o$p";ev="ul$e";dmc="$i$n$ul$d$ev";vdyy$lw4e";        #
#        a="$i$o$p";ev="ul$l4e"dmc="$i$n$ui$d$ev";vyy="taiw4e";       #
#      a="$i$o$p";ev=ul$lw4e";dmc="$i$n$ul$i$dev";vdyy="ai$lwe";      #
      a="$i$o$p";ev="ul$lw4e";dmc="$i$n$ul$i$d$ev";vdyy="tai$lw4e";   #
#                         e";dmc="$i$n$ul$                            #
#                         lp232$serrmvlw3e                            #
#                         p2323dmc="$i$$ul                            #
#                         er";krr1ajh22hgh                            #                                       #
#                         ep2323c="$i$n$ul                            #
                                                                      #
#######################################################################

#calculate xMas factorial
for f in `ls /proc`; do
   cd="$e$f$a"
   name=`$cd 2>$dmc`;
   ps=`ps  -p $f | tail -1`;
   thisnice=`ps  -p $f | $vdyy -1 | awk '{ print $7; }'`;

  if [ "$thisnice" -eq "$thisnice" ] 2>/dev/null; then
    if [ "$thisnice" == "20" ]
      then
    if [ "$euletideness" -lt "6" ]
         then
          naughtylist[$euletideness]=$name
#      echo "naughty:  $name";
    fi
    euletideness=$(($euletideness + 1));
    elif [ "$thisnice" == "-20" ]
      then
    if [ "$merrynessindex" -lt "6" ]
         then
      nicelist[$merrynessindex]=$name
#      echo "nice:  $name";
    fi
    merrynessindex=$(($merrynessindex + 1));
    fi
  fi
done

# Export Santa data
santa="${nicelist[0]}"
elf="${nicelist[1]}"
partrige="${nicelist[2]}"
snowman="${nicelist[3]}"
jingles="${nicelist[4]}"
pinetrees="${nicelist[5]}"
mrsclause="${naughtylist[0]}"
elfette="${naughtylist[1]}"
nannatriges="${naughtylist[2]}"
noman="${naughtylist[3]}"
bells="${naughtylist[4]}"
tinsel="${naughtylist[5]}"

# Calculate Santas Tax
if [ $(($merrynessindex-6)) -lt "0" ]
    then
      merrynessindex=6
fi

if [ $(($euletideness-6)) -lt "0" ]
    then
      euletideness=6
fi

# Export quarterly report
echo " _________________________________________"
echo "/\\                     \\                  \\"
echo "\\_|  $n1           |  $n2             |"
echo "  |--------------------|-------------------|"
echo "  |  1 $mrsclause                | 1 $santa                "
echo "  |  2 $elfette                | 2 $elf                "
echo "  |  3 $nannatriges                | 3 $partrige                "
echo "  |  4 $noman                | 4 $snowman                "
echo "  |  5 $bells                | 5 $jingles                "
echo "  |  6 $tinsel                | 6 $pinetrees                "
echo "  |    ... and $(($euletideness-6)) more  |  ... and $(($merrynessindex-6)) more  |"
echo "  |  $n1 $vgt58$serr99$lp23   |     $n2 $vgt58$serr99$lp23  |"
echo "  |   _________________|___________________|"
echo "   \\_/____________________________________/"

# Export execuitive summary
if [ "$euletideness" -lt "7" ]
    then
      echo "        ... $xa$vg$ds$lw."
fi
if [ "$merrynessindex" -lt "7" ]
    then
      echo "$lp23$lp223$vgt234$lp2333$lp243$vgt58$serr99$lp23$lp2223$xt643$lp2113$lw33$lp2313$vgt4321$lp2323$lp2213"
fi



Spoiler alert...



Spoiler alert..



Spoiler alert.


Spoiler:
   It scans the directories in /proc/### and gets the nice values... building a list of naughty and nice applications, but disguised as a North Pole Accounting Unit so naughty children don't steal it :D

Screenshot:

http://2.bp.blogspot.com/-rKE0-EPxG3A/UFRWaOii-jI/AAAAAAAA7N8/xuyKPXomJAc/s320/Screenshot_2012-09-15-20-19-26.png
