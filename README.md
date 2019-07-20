# VIDEOSTORE
работающий код
#include <iostream>
#include <Windows.h>

using namespace std;

struct VideoStore
{
	char name[40];
	char director[30];
	char genre[15];
	double rating;
	double price;

};

VideoStore a[124] = { { "Зелёная книга","Питер Фаррелли","Биография",8.68,253.7},
 { "Собачья жизнь","Лассе Халльстрём","Семейные",9.05,215.35 },
 { "Семь Жизней","Габриэле Муччино","Драмы",8.87,185.5 },
 { "Девушка моих кошмаров","Питер Фаррелли","Комедия",6.25 ,143.8},
 { "Время","Эндрю Никкол","Фантастика",8.54,180.5 },
 { "Исходный код","Дункан Джонс","Фантастика",8.5,175.3 },
 { "Эффект бабочки","Эрик Бресс","Фантастика",8.47,154.5 },
 { "Мотылёк","Михаэль Ноер","Триллер",8.69,260.9 },
 { "Забирая жизни","Джей Крузо","Детектив",7.97,163.1 },
 { "Копы в Юбках","Пол Фейг","Комедия",7.98,160.5 },
 { "Все без ума от Мэри","Питер Фаррелли","Комедия",5.7,125.35 },
 { "Все деньги мира","Ридли Скот","Биография",7.88,152.7 },
 { "Шоколад","Лассе Хальстрём","Драма",8.9 ,172.3 },
 { "Мужчина нарасхват","Габриэле Муччино","Комедия",7.5,157.2 },
 { "Шпион","Пол Фейг","Боевик",6.9,151.3},
 { "Необъявленный","Пол Фейг","Комедия",8.3,157.2},
 { "Легенда","Ридли Скот","Фэнтези",7.5,132.8},
 { "Иван Васильевич меняет профессию","Леонид Гайдай","Комедия",9.8,115.5},
 { "Статский советник","Филипп Янковский","Детектив",8.5,95.3},
 { "Звездные войны 1: Скрытая угроза","Джордж Лукас","Фантастика",8.1,120.72},
 { "Галактика THX-1138","Джордж Лукас","Драма",3.3,54.2},
 { "Меченосец","Филипп Янковский","Триллер",5.7,105.6},
 { "Не может быть","Леонид Гайдай","Комедия",9.7,110.25},
 { "Оцепеневшие от страха","Демиан Рунья","Ужасы",8.68,180.5 } };

void Show(int N)
{
	cout << a[N].name << ", ";
	cout << a[N].director << ", ";
	cout << a[N].genre << ", ";
	cout << a[N].rating << ", ";
	cout << a[N].price << " \n";

}

int main()
{
	int x,z;
	int numDisc = 24;
	const int size = 50;
	char string[size];//начальная строка вводимая пользователем
	bool filmOk, genreOk, directorOk, Exit = 0;
	int bestInGenre=-1;

	//setlocale(LC_CTYPE, ".866");
	//setlocale(LC_CTYPE, "rus");
	
	SetConsoleCP(1251);
	SetConsoleOutputCP(1251);
	
	while (1)
	{
		system("cls");
		do
		{
			cout << "\t" << "Для поиска желаемого  фильма нажмите : 1 \n";
			cout << "\t" << "Для поиска  фильмов определенного жанра  нажмите : 2 \n";
			cout << "\t" << "Для поиска  фильма конкретного режисера  нажмите : 3 \n";
			cout << "\t" << "Для поиска самого популярного  фильма  в жанре нажмите : 4 \n";
			cout << "\t" << "Для просмотра  списка всех фмльмов нашего магазина  нажмите : 5 \n";
			cout << "\t" << "Если вы сотрудник нашего магазина и желаете дополнить нашу фильмотеку нажмите : 6 \n";
			cout << "\t" << "Выход из программы : 7 \n";
cout<"@  @   @   @   @   @   @   @   @  @   @   @   @   @"<<endl;
			cout << "\t\t\t"; cin >> x;
			if (x <= 0 || x > 7)
			{
				cout << "\t Ошибка ! ! ! \n";
			}

		} while (x <= 0 || x > 7);


		switch (x)
		{
		case 1:
			cout << "\t Введите название фильма : \n";
			cin.ignore();
			gets_s(string);

			filmOk = 0;

			for (int i = 0; i < numDisc; i++)
			{
				bool Ok = 1;
				for (int j = 0; j < strlen(string); j++)
				{
					if (string[j] != a[i].name[j])
					{
						Ok = 0;
						break;
					}
				}

				if (Ok == 1)
				{
					Show(i);
					filmOk = 1;
				}

			}
			if (filmOk == 0)
			{
				cout << "Фильм не нейден" << "\n";
			}

			/*filmOk = 0;
			for (int i = 0; i < 24; i++)
			{
				if (strcmp(string,a[i].name) == 0)
				{
					Show(i);
					filmOk = 1;
				}
			}

			if (filmOk == 0)
			{
				cout << "Фильм не нейден" << "\n";
			}
	*/
	// int strcmp(const char *s1, const char *s2);
	//— Сравнивает две строки.Возвращает отрицательное значение,
	//если s1 < s2; нуль, если s1 == s2; положительное значение, если s1 > s2.Параметры — указатели на сравниваемые строки

			break;
		case 2:
			cout << "\t Введите название жанра  : \n";
			cin.ignore();
			gets_s(string);

			genreOk = 0;
			for (int i = 0; i < numDisc; i++)
			{
				if (strcmp(string, a[i].genre) == 0)
				{
					Show(i);
					genreOk = 1;
				}
			}

			if (genreOk == 0)
			{
				cout << "Жанр не нейден" << "\n";
			}


			break;
		case 3:


			cout << "\t Введите имя ражисёра  : \n";
			cin.ignore();
			gets_s(string);

			directorOk = 0;
			for (int i = 0; i < numDisc; i++)
			{
				if (strcmp(string, a[i].director) == 0)
				{
					Show(i);
					directorOk = 1;
				}
			}

			if (directorOk == 0)
			{
				cout << "Режисёр не найден" << "\n";
			}


			break;
		case 4:
			cout << "\t Введите название жанра  : \n";
			cin.ignore();
			gets_s(string);

			for (int i = 0; i < numDisc; i++)
			{
				if (strcmp(string, a[i].genre) == 0)
				{
					if (bestInGenre >= 0)
					{
						if (a[i].rating > a[bestInGenre].rating)
						{
							bestInGenre = i;
						}
					}
					else
					{
						bestInGenre = i;
					}

				}

			}

			if (bestInGenre == -1)
			{
				cout << "Жанр не нейден" << "\n";
			}
			else
			{
				Show(bestInGenre);
			}


			break;
		case 5:

			for (int i = 0; i < numDisc; i++)
			{
				Show(i);
				cout << "\n";
			}


			break;
		case 6:
			cout << "\t" << "Введите пароль : \n";//3597
			cout << "\t\t\t"; cin >> z;
			if (z==3597)
			{
				cout << "\t" << "Введите название нового фильма : \n";
				cin.ignore();
				gets_s(string);
				strcpy_s(a[numDisc].name, 40, string);

				cout << "\t" << "Введите имя режисёра : \n";
				gets_s(string);
				strcpy_s(a[numDisc].director, 30, string);

				cout << "\t" << "Введите жанр фильма : \n";
				gets_s(string);
				strcpy_s(a[numDisc].genre, 15, string);

				cout << "\t" << "Введите рейтинг : \n";
				cin >> a[numDisc].rating;
				cout << "\t" << "Введите стоимость диска : \n";
				cin >> a[numDisc].price;
				    numDisc++;

			}
			else
			{
				cout << "\t" << "У вас нет прав доступа !\n";
			}
			break;

		case 7:

			Exit = 1;


			break;

		default:
			break;
		}

		if (Exit==1)
		{
			break;

		}

cout<<"@   @   @   @   @   "<<endl;
		system("pause");
	}




	
	return 0;
}
