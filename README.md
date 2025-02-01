/* Write a program to create, read, write and append data to a file. * /
 #include<stdio.h>
   #include<stdlib.h>
    void create_file(const char *filename)
    {
            FILE *file = fopen(filename,"w");
           if(file == NULL)
           {
                   printf("\e[31mError: Could not create file.\e[0m\n");
                 return;
          }
         printf("\e[32mFile created successfully!\e[0m\n");
          fclose(file);
  }
  void write_file(const char *filename)
  {
          FILE *file = fopen(filename,"w");
           if(file == NULL)
           {
                   printf("\e[31mError: Could not open file for writing.\e[0m\n");
                   return;
           }
           char data[100];
           printf("Enter data to write to the file: ");
           getchar();
           fgets(data,sizeof(data),stdin);
           fprintf(file,"%s",data);
           printf("\e[32mData written successfully!\e[0m\n");
           fclose(file);
  }
 void append_file(const char *filename)
 {
         FILE *file = fopen(filename,"a");
        if(file == NULL)
          {
                  printf("\e[31mError: Could not open file for appending.\e[0m\n");
                  return;
         }
          char data[100];
          printf("Enter data to append to the file: ");
         getchar();
          fgets(data,sizeof(data),stdin);
          fprintf(file,"%s",data);
          printf("\e[32mData appended successfully.\e[0m\n");
         fclose(file);
  }
void read_file(const char *filename)
  {
          FILE *file = fopen(filename,"r");
         if(file == NULL)
          {
                 printf("\e[31mError: Could not open file for reading.\e[0m\n");
                 return;
         }
          char ch;
        printf("File contents:\n");
         while((ch=fgetc(file)) != EOF)
         {
                  putchar(ch);
         }
         fclose(file);
  }
int main()
 {
        char filename[50];
         int choice;
        printf("Enter the file name: ");
         scanf("%s",filename);
          do{
                  printf("\n\e[33mFile Operations Menu:\e[0m\n");
                 printf("\e[36m1. Create File\n");
                  printf("2. Write to File\n");
                  printf("3. Append File\n");
                 printf("4. Read File\n");
                  printf("5. Exit\e[0m\n");
                 printf("entre your choice:");
                 scanf("%d",&choice);
                  switch(choice)
                  {
                         case 1: create_file(filename);
                                break;
                        case 2: write_file(filename);
                                  break;
                          case 3: append_file(filename);
                                  break;
                         case 4: read_file(filename);
                                  break;
                         case 5: printf("\e[32mExiting program...\e[0m\n");
                                break;
                        default: printf("\e[31mInvalid choice.Try again.\e[0m\n");
             }
       } while(choice!=5);
          return 0;
  }
