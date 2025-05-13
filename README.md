Вариант:
Объявление перечисления в СУБД PostgreSQL

Примеры:
create type request_state as enum ('created', 'approved', 'finished');
create type request_state as enum ();

Определим грамматику перечисления языка PostgreSQL G[<C>]в нотации Хомского с продукциями P:
	<C> → ‘create’ <space1>
	<space1> → ‘ ‘ <keyword1>
	<keyword1> → ‘type’ <space2>
	<space2> → ‘ ‘ <ID>
	<ID> → <letter> <IDrem>
	<IDrem> → <letter> <IDrem>  | <digit> <IDrem>
	<IDrem> → ‘ ‘ <space3>
	<space3> → ’as’ <keyword2>
	<keyword2> → ‘ ‘ <space4>
	<space4> → ‘enum’ <keyword3>
	<keyword3> → ‘(‘ <open_bracket>
	<open_bracket > → ‘)’ <end>
	<open_bracket> → ‘'’ <string_open>
	<string_open> → <letter> <stringrem>
	<stringrem> → <letter> <stringrem> | <digit> <stringrem>
	<stringrem> →  ‘'’ <string_close>
	<string_close> → ‘,’ <open_bracket>
	<string_close> → ‘)’ <end>
	<end> → ‘;’ 

<letter> -> ‘a’ | ‘b’ | ‘c’ |…| ‘y’ | ‘z’ | ‘A’ | ‘B’ | ‘C’ |…| ‘Y’ | ‘Z’
<digit> -> ‘0’ | ‘1’ | ‘2’ | ‘3’ | ‘4’ | ‘5’ | ‘6’ | ‘7’ | ‘8’ | ‘9’
Следуя введенному формальному определению грамматики, представим G[<C>] ее составляющими:
	Z= <C>;
	V_T={a,b,c,…,y,z,A,B,C,… ,Y,Z,(,),'',,,;,0,1,2,...,8,9};
	V_N={<C>,<space1>,<keyword1>,<space2>,<ID>,<IDrem>,<space3>,<keyword2>,<open_(_bracket)>,<string_(_open)>,<stringrem>,<space4>,<keyword3>,<end>,<letter>,<digit>}

 Классификация грамматики:
	Согласно классификации Хомского, грамматика G[<C>] является автоматной, так как удовлетворяет определению:
G[A]:A→aB |a |  ε,a∈V_T,A,B∈V_N.
Все правила (1)-(19) относятся к классу праворекурсивных продукций. 

Граф конечного автомата:
![image](https://github.com/user-attachments/assets/47ba1ad1-dfe8-423e-a4a6-10588448c14a)

тестовые примеры:
![image](https://github.com/user-attachments/assets/8f4bc955-3e83-4816-a6cc-13d3d9dfded5)

![image](https://github.com/user-attachments/assets/444acea8-1557-4c99-a00a-4cadc6bbe0af)


[РГР Компиляторы.docx](https://github.com/user-attachments/files/20184891/default.docx)



