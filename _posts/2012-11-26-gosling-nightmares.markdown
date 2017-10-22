---
layout: post
title:  "A Device to Give Gosling Nightmares"
date:   2012-11-26 19:37:56 +1100
categories: article
---


Making up for the long delay between my last two posts, here's another one mere hours after the last, and this time with code!
:D So, I've been reading about Duff's device (http://www.lysator.liu.se/c/duffs-device.html and http://stackoverflow.com/questions/514118/how-does-duffs-device-work#514289) and loop unrolling (http://en.wikipedia.org/wiki/Loop_unwinding), and wanted to have a crack at it in Java... well of course there is absolutely no point implementing this in Java, and the results are just as I expected... the JVM can optimize a normal loop better than it can an unrolled loop :p ... I've even heard that every time a developer unwinds a loop in Java, James Gosling gets a headache... sorry James.

Still it was a good interesting exercise... I challenge you all to implement an unrolled loop in your language of choice! I'd love to see a lisp version, actually on second thoughts...

Anyhow, here it is:

//(c)me & GPL3:
public class DuffsDevice
{
  public static void main(String[] args)
  {
    int demoSize = 80;//woot... 0 works
    System.out.println("Normal loop: "  );
    long start = System.nanoTime();
    for(int i = 0; i < demoSize; i++)// one partial two full for demo
    {
      System.out.print(" Bit:" + i);
    }//normal loop
    System.out.println("\nNormal  end: " + (System.nanoTime()-start));

    final int winding = 5;//up to 6
    System.out.println("Duffs device in Java loop: ");
    start = System.nanoTime();
    for(int i = 0; i < demoSize; i = i)// one partial two full for demo
    {
      System.out.print("\n" );//System.out.println("size%winding:" + demoSize%winding + "  i:" + i  );
      switch( (i + winding <= demoSize) ? 0 : winding-(demoSize%winding) )
      {
        //case (winding-6): { System.out.print(" Bit:" + (i) +" -a" ); i++; }
        case (winding-5): { System.out.print(" Bit:" + (i) +" -b" ); i++; }
        case (winding-4): { System.out.print(" Bit:" + (i) +" -c" ); i++; }
        case (winding-3): { System.out.print(" Bit:" + (i) +" -d" ); i++; }
        case (winding-2): { System.out.print(" Bit:" + (i) +" -e" ); i++; }
        case (winding-1): { System.out.print(" Bit:" + (i) +" -f" ); i++; }
      }//switch
    }//Duffs device
    System.out.println("\nDuffs device in Java  end: " + (System.nanoTime()-start));
    //usually arround 1803034 in the normal loop
    //usually arround 2272790(winding 3) 2065498(winding 6) for unrolled loop... ymmv of course.
    //Duff was right... this is even pretty ugly in Java :p ... ugly, but fun :D
  }//main
}//class


Hope you enjoyed reading, I especially liked the embedded conditional statement as the switch control statement... writing that bit really got my heart racing haha


I got (sort of ... not realy) Slashdoted!
  Again it's been a while, but this time I was just sick... still that didn't stop lot of things happening.
   First of let's address the title of this post: I got Slashdoted, well sort of... 11 hits is a lot for a 30 minute video of a guy using Gimp (badly) for simple editing, haha (https://www.youtube.com/watch?v=gBrMR9HrF5w&list=UU0Px8r1nMNPVHn4sFYnMkfg&index=3&feature=plcp). I entered the Slashdot 15th anniversary logo competition and came first! was picked for the first day of the month (http://slashdot.org/logo15.pl), haha... anyhow my logo was a little endian joke (dot slash) with an insensitive clod reference thrown in for good measure. I love the "insensitive clod" poll options, I so often pick them.

I also wrote an email to MrDr Heinz Max Kabutz (of Java Specialists newsletter)... detailing what I thought was an interesting difference between Androids handling of the compilation routine and the way Java does it (http://www.javaspecialists.eu/archive/Issue050.html). I was partially so interested in the topic as I was under the impression little to no pre-compilation was performed on java code, so to learn about any java pre-compilation was interesting but to then realize that Android and Java both use different pre-compilation routines was somewhat more interesting. Hans got back to me, but unfortunately didn't know about the Android compiler. This has left me with a lingering desire to learn more about precompilation in java so lookout for coverage of that in the future.

 Dr Kabutzs example:

public class A1 {
  Character aChar = new Character('\u000d');
}





In addition I also received a charming but somewhat disturbing email from a Mr. Shaun P. who was concerned that because I had licensed code used in a tutorial as GPL anyone following that tutorial would be forced to licence anything they wrote using that technique as GPL. Besides the viral nature of the GPL being half the point of the whole licence, I would have thought someone's use of my code would have to be substantial and direct for me to claim it as a derivative work... simply using the same technique or a small chunk would simply not suffice. Remember, Linus does not even consider Bionic to be a derivative work. I also began creating solutions to the Project Euler problems in the form of Android applications. Checkout Euler 1 and Euler 2 on the Play Store now. Euler 3 is in the works, but it's a step learning curve between problems two and three.

While recovering from illness and in a state of total delirium I created a funny little video in tribute to Melencolia 1 (http://www.youtube.com/watch?v=0gtAJL4bKGk&lc=mwStJrKCNr1Wua-Vn2-V8zayxcrRakbh3lNOBtGXRlw&lch=email&feature=em-comment_received) which was introduced to me by ... from the Numberfile videos (http://www.youtube.com/watch?v=gGvyeuDT2Do&feature=related), absolutely worth checking out if you haven't yet.

and finally: What the hell is up with those BSD guys? (http://old.nabble.com/Real-men-don%27t-attack-straw-men-tt14256924r0.html) I just can't fathom how patient and polite Richard Stallman is... the background to this is that bsd got removed from the fsf list of endorsed projects and Stallman vaguely implied that they promote proprietary software. Well, the bsd guys were tearing into Stallman in this forum demanding an apology or something. Anyhow I think Stallman comes of looking professional and (overly) polite, what do you all think out there?
