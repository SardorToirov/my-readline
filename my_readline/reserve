#include <stdio.h>
#include <fcntl.h>
#include <string.h>
#include <unistd.h>
#include <stdlib.h>
#include <stdio.h>

int READLINE_READ_SIZE = 20;

char* my_readline(int fd){
    char c;
    char* string=(char*)malloc(READLINE_READ_SIZE);
    int i=0,j;
    while ((j=read(fd,&c,1))>=0){
        if(j==0){
            if((int)strlen(string) > 0)
                return string;
            else
                return NULL;
        }
        if(c=='\n'){
            return string;
        }else{
            if(i < READLINE_READ_SIZE){
                string[i++]=c;
            }
        }
    }
    return NULL;

}

int main(int ac, char **av)
{
  char *str = NULL;

  int fd = open(av[1], O_RDONLY);
  while ((str = my_readline(fd)) != NULL)
  {
      printf("%s\n", str);
      free(str);
  }
  close(fd);

  //  Yes it's also working with stdin :-)
  //  printf("%s", my_readline(0));
  return 0;
}