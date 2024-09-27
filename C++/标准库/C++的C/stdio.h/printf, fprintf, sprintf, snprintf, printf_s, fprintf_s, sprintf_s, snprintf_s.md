| **int printf( const char *format, ... );**                                                                         | (1)     | **(until C99)** |
| ------------------------------------------------------------------------------------------------------------------ | ------- | --------------- |
| **int printf( const char *restrict format, ... );**                                                                | **(1)** | **(since C99)** |
| **int fprintf( FILE *stream, const char  *format, ... );**                                                         | **(2)** | **(until C99)** |
| **int fprintf( FILE *restrict stream, const char *restrict format, ... );**                                        | **(2)** | **(since C99)** |
| **int sprintf( char *buffer, const char  *format, ... );**                                                         | **(3)** | **(until C99)** |
| **int sprintf( char *restrict buffer, const char *restrict format, ... );**                                        | **(3)** | **(since C99)** |
| **int snprintf( char *restrict buffer, size_t bufsz,  <br>              const char *restrict format, ... );**      | **(4)** | **(since C99)** |
| **int printf_s( const char *restrict format, ... );**                                                              | **(5)** | **(since C11)** |
| **int fprintf_s( FILE *restrict stream, const char *restrict format, ... );**                                      | **(6)** | **(since C11)** |
| **int sprintf_s( char *restrict buffer, rsize_t bufsz,  <br>               const char *restrict format, ... );**   | **(7)** | **(since C11)** |
| **int snprintf_s( char *restrict buffer, rsize_t bufsz,  <br>                const char *restrict format, ... );** | **(8)** | **(since C11)** |
