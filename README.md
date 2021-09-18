#include <stdio.h>
#include <conio.h>

char arr[10] = {'_', '_', '_','_', '_', '_','_', '_', '_'};
char person = 'X';
bool condition = true;


// board...
void board( char arr[])
{
	printf("%c|%c|%c\n", arr[0], arr[1], arr[2]);
	printf("%c|%c|%c\n", arr[3], arr[4], arr[5]);
	printf("%c|%c|%c\n", arr[6], arr[7], arr[8]);
}


// user input...
void input()
{
	int inp;
	printf("Enter a number between 1 & 9  ");
	scanf("%d",&inp);

	if (arr[inp - 1] != '_')
	{
	printf("Already exist\n");
	}
	else
	{
		arr[inp - 1] = person;
		board(arr);
	}
}


// Checking tie...
void check_tie()
{
	if (arr[0] != '_' && arr[1] !='_'&& arr[2] !='_' && arr[3] != '_' && arr[4] != '_' && arr[5] != '_' && arr[6] != '_' && arr[7] != '_' && arr[8] != '_')
	{
		printf("\nGAME TIE\n");
		condition = false;
	}
}


// Checking vertical...
void vertical()
{
	if (arr[0] == person && arr[1] == person && arr[2] == person)
	{
		printf("%c won\n", person);
		condition = false;
	}
	else if (arr[3] == person && arr[4] == person && arr[5] == person)
	{
		printf("%c won\n", person);
		condition = false;
	}
	else if (arr[6] == person && arr[7] == person && arr[8] == person)
	{
		printf("%c won\n", person);
		condition = false;
	}
}


// Checking Horizontal...
void horizontal()
{
	if (arr[0] == person && arr[3] == person && arr[6] == person)
	{
		printf("%c won\n", person);
		condition = false;
	}
	else if (arr[1] == person && arr[4] == person && arr[7] == person)
	{
		printf("%c won\n", person);
		condition = false;
	}
	else if (arr[2] == person && arr[5] == person && arr[8] == person)
	{
		printf("%c won\n", person);
		condition = false;
	}
}


// Checking Diagonal..
void diagonal()
{
	if (arr[0] == person && arr[4] == person && arr[8] == person)
	{
		printf("%c won\n", person);
		condition = false;
	}
	else if (arr[2] == person && arr[4] == person && arr[6] == person)
	{
		printf("%c won\n", person);
		condition = false;
	}
}


// check win...
void check_win()
{
	vertical();
	horizontal();
	diagonal();
}


// check game...
void check_game()
{
	check_win();
	check_tie();
}

void game_flip()
{
	if (person == 'X')
	{
		person = 'O';
	}
	else if (person == 'O')
	{
		person = 'X';
	}
}


// MAIN FUNCTION...
int main()
{
	board(arr);

	while (condition)
	{
		input();

		check_game();
		game_flip();
	}
}
