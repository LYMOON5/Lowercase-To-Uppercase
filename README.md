#include<stdio.h>
#include<assert.h>
#include<ctype.h>

小写字母转大写字母然后保存到test文件中
void ToUp(const char *path,char *str)
{
	assert(path != NULL && str != NULL);//判断打开成功

	FILE *fw = fopen(path,"w");
	assert(fw != NULL);
	char ch;

	while(*str != '\0')
	{
		if(islower(*str))
		{
			ch = toupper(*str);
			fwrite(&ch,sizeof(char),1,fw);
		}
		else
		{
			fwrite(str,sizeof(char),1,fw);
		}
		str++;
	}
	fclose(fw);
}

int main()
{
	char *path = "H:\\1.txt";
	ToUp(path,"abcde123FGHijk");
  
	return 0;
}
