Parfois le texte est bien imprimé, et parfois il beug.
Il rentre dans une boucle "infinie" lorsque le avec "cc -Wall -Wextra -Werror main.c get_next_line_utils.c get_next_line.c -D BUFFER_SIZE=10000000"
Je dirais que c'est une histoire de buffer et d'allocation memoire. 
Parfois la meme compilation mais plusieurs sorties de a.out differentes ne donne pas le meme resultat.

 -fsanitize=address renvoie
 ==30417==ERROR: AddressSanitizer: heap-buffer-overflow on address 0x61b000000d8e at pc 0x00010f5f4159 bp 0x7ffee060e6b0 sp 0x7ffee060e6a8
WRITE of size 1 at 0x61b000000d8e thread T0
    #0 0x10f5f4158 in ft_strjoin+0x188 (a.out:x86_64+0x100003158)
    #1 0x10f5f45b6 in get_next_line+0xb6 (a.out:x86_64+0x1000035b6)
    #2 0x10f5f3d45 in main+0x55 (a.out:x86_64+0x100002d45)
    #3 0x7fff6779dcc8 in start+0x0 (libdyld.dylib:x86_64+0x1acc8)

0x61b000000d8e is located 0 bytes to the right of 1550-byte region [0x61b000000780,0x61b000000d8e)
allocated by thread T0 here:
    #0 0x10f65017d in wrap_malloc+0x9d (libclang_rt.asan_osx_dynamic.dylib:x86_64h+0x4917d)
    #1 0x10f5f4438 in ft_calloc+0x28 (a.out:x86_64+0x100003438)
    #2 0x10f5f4018 in ft_strjoin+0x48 (a.out:x86_64+0x100003018)
    #3 0x10f5f45b6 in get_next_line+0xb6 (a.out:x86_64+0x1000035b6)
    #4 0x10f5f3d45 in main+0x55 (a.out:x86_64+0x100002d45)
    #5 0x7fff6779dcc8 in start+0x0 (libdyld.dylib:x86_64+0x1acc8)
