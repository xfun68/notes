notes
=====

http://stackoverflow.com/a/5699483

```c++
void printStack( void );
void printStack( void )
{
     unsigned int   i;
     void         * stack[ 100 ];
     unsigned short frames;
     SYMBOL_INFO  * symbol;
     HANDLE         process;

     process = GetCurrentProcess();

     SymInitialize( process, NULL, TRUE );

     frames               = CaptureStackBackTrace( 0, 100, stack, NULL );
     symbol               = ( SYMBOL_INFO * )calloc( sizeof( SYMBOL_INFO ) + 256 * sizeof( char ), 1 );
     symbol->MaxNameLen   = 255;
     symbol->SizeOfStruct = sizeof( SYMBOL_INFO );

     for( i = 0; i < frames; i++ )
     {
         SymFromAddr( process, ( DWORD64 )( stack[ i ] ), 0, symbol );

         printf( "%i: %s - 0x%0X\n", frames - i - 1, symbol->Name, symbol->Address );
     }

     free( symbol );
}
```

http://stacktrace.sourceforge.net/


http://dirlt.com/tcmalloc.html

http://goog-perftools.sourceforge.net/doc/tcmalloc.html

http://blog.csdn.net/jhzhou/article/details/7245992
http://google-perftools.googlecode.com/svn/trunk/doc/heapprofile.html

http://google-perftools.googlecode.com/svn/trunk/doc/cpuprofile.html


http://lemire.me/blog/archives/2012/06/20/do-not-waste-time-with-stl-vectors/
