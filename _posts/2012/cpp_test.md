---
    layout: post
    title: code highlight test
    tagline:
    tags: [test, test2] 
---
##python## 
{%highlight python%}
class ExitNotifyThread(Thread):
    """This class is designed to alert a "monitor" to the fact that a thread has
    exited and to provide for the ability for it to find out why."""
    def run(self):
        global exitthreads, profiledir
        self.threadid = thread.get_ident()
        try:
            if not profiledir:          # normal case
                Thread.run(self)
            else:
                try:
                    import cProfile as profile
                except ImportError:
                    import profile
                prof = profile.Profile()
                try:
                    prof = prof.runctx("Thread.run(self)", globals(), locals())
                except SystemExit:
                    pass
                prof.dump_stats( \
                            profiledir + "/" + str(self.threadid) + "_" + \
                            self.getName() + ".prof")
        except:
            self.setExitCause('EXCEPTION')
            if sys:
                self.setExitException(sys.exc_info()[1])
                tb = traceback.format_exc()
                self.setExitStackTrace(tb)
        else:
            self.setExitCause('NORMAL')
        if not hasattr(self, 'exitmessage'):
            self.setExitMessage(None)

        if exitthreads:
            exitthreads.put(self, True)

    def setExitCause(self, cause):
        self.exitcause = cause
    def getExitCause(self):
        """Returns the cause of the exit, one of:
        'EXCEPTION' -- the thread aborted because of an exception
        'NORMAL' -- normal termination."""
        return self.exitcause
    def setExitException(self, exc):
        self.exitexception = exc
    def getExitException(self):
        """If getExitCause() is 'EXCEPTION', holds the value from
        sys.exc_info()[1] for this exception."""
        return self.exitexception
    def setExitStackTrace(self, st):
        self.exitstacktrace = st
    def getExitStackTrace(self):
        """If getExitCause() is 'EXCEPTION', returns a string representing
        the stack trace for this exception."""
        return self.exitstacktrace
    def setExitMessage(self, msg):
        """Sets the exit message to be fetched by a subsequent call to
        getExitMessage.  This message may be any object or type except
        None."""
        self.exitmessage = msg
    def getExitMessage(self):
        """For any exit cause, returns the message previously set by
        a call to setExitMessage(), or None if there was no such message
        set."""
        return self.exitmessage
{% endhighlight%}

##Cpp##
{%highlight cpp%}
#include <ctime>
#include <iostream>
#include <string.h>
#include <stdio.h>
#include <cstdio>
 
 
template<typename T> void sink(T const& t) {
   volatile T sinkhole = t;
}
 
#define LOOP_COUNT 0xFFFFFF
 
void strncpy_test()
{
	volatile char buf[128];
	volatile char teststr[] = "this is a test string";
	for(unsigned int i=0; i<LOOP_COUNT;i++)
	{
		strncpy((char*)buf, (char*)teststr, sizeof(buf));
	}
}
 
void strcpy_test()
{
	volatile char buf[128];
	volatile char teststr[] = "this is a test string";
	for(unsigned int i=0; i<LOOP_COUNT;i++)
	{
		strcpy((char*)buf, (char*)teststr);
	}
}
 
void strcpy_check_test()
{
	volatile char buf[128];
	volatile char teststr[] = "this is a test string";
	for(unsigned int i=0; i<LOOP_COUNT;i++)
	{
		if(strlen((char*)teststr) + 1 < sizeof(buf))
			strcpy((char*)buf, (char*)teststr);
	}
}
 
 
void sprintf_s_test()
{
	volatile char buf[128];
	volatile char teststr[] = "this is a test string";
	for(unsigned int i=0; i<LOOP_COUNT;i++)
	{
		sprintf_s((char*)buf, sizeof(buf), "%s", (char*)teststr);
	}
}
 
 
void snprintf_test()
{
	volatile char buf[128];
	volatile char teststr[] = "this is a test string";
	for(unsigned int i=0; i<LOOP_COUNT;i++)
	{
		_snprintf((char*)buf, sizeof(buf), "%s", (char*)teststr);
	}
}
 
 
 
void stdstring_test()
{
	std::string buf;
	std::string teststr("this is a test string");
	for(unsigned int i=0; i<LOOP_COUNT;i++)
	{
		buf = teststr;
	}
	sink(buf);
}
 
int main(int argc, char *argv[])
{
	std::clock_t start;
    double duration;
 
	// Warm up
	strncpy_test();
 
	// Real run
	start = std::clock();
    strncpy_test();
	duration = ( std::clock() - start ) / (double) CLOCKS_PER_SEC;
 
	std::cout << "strncpy: " << duration << std::endl;
 
 
 
	// Warm up
	strcpy_check_test();
 
	// Real run
	start = std::clock();
    strcpy_check_test();
	duration = ( std::clock() - start ) / (double) CLOCKS_PER_SEC;
 
	std::cout << "strcpy_check: " << duration << std::endl;
 
 
	// Warm up
	strcpy_test();
 
	// Real run
	start = std::clock();
    strcpy_test();
	duration = ( std::clock() - start ) / (double) CLOCKS_PER_SEC;
 
	std::cout << "strcpy: " << duration << std::endl;
 
 
 
 
	// Warm up
	stdstring_test();
 
	// Real run
	start = std::clock();
    stdstring_test();
	duration = ( std::clock() - start ) / (double) CLOCKS_PER_SEC;
 
	std::cout << "std::string: " << duration << std::endl;
 
	// Warm up
	snprintf_test();
 
	// Real run
	start = std::clock();
    snprintf_test();
	duration = ( std::clock() - start ) / (double) CLOCKS_PER_SEC;
 
	std::cout << "snprintf: " << duration << std::endl;
 
 
	// Warm up
	sprintf_s_test();
 
	// Real run
	start = std::clock();
    sprintf_s_test();
	duration = ( std::clock() - start ) / (double) CLOCKS_PER_SEC;
 
	std::cout << "sprintf_s: " << duration << std::endl;
 
	system("pause");
}
{%endhighlight%}

##C# ##
{%highlight csharp%}
using UnityEngine;
using System.Collections;
[System.Serializable]
public class MyPlayer : MonoBehaviour 
{
	public int armor  = 75;
	public int damage = 75;
	public GameObject gun; 
}
{%endhighlight%}
