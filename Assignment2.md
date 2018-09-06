
 Show that p->q and q' -> p' are logically equivalent without using truth tables or a "contrapositive" law (don't assume they are true)
 ---
    p->q <=> q' -> p'
    'p v q <=> ('q)' v p'     Implication
    'p v q <=> q v p'         Double Negation
    'p v q <=> 'p v q         Communinative
 
 Show that (p->r) ^ (q->r) <=> (p v q) -> r
 ---
    (p->r) ^ (q->r) <=> (p v q) -> r
    ('p v r) ^ ('q v r) <=> (p v q) -> r   Implication
    (r v 'p) ^ (r v 'q) <=> (p v q) -> r   Communiative
    r v ('p ^ 'q) <=> (p v q) -> r         Distributive
    ('p ^ 'q) v r <=> (p v q) -> r         Communiative
    (p v q)' v r <=> (p v q) -> r          DeMorgan's Law
    (p v q) -> r <=> (p v q) -> r          Implication
 
 Give an interpretation to prove that the following wff is not valid: (Ǝx)A(x) ^ (Ǝx)B(x) -> (Ǝx)(A(x) ^ B(x))
 ---
      if x = programmers, A(x) = programmers who use the light theme, B(x) = programmers who use the dark theme
      Some programmers use the light theme, and some programmers use the dark theme.
      That does not mean that programmers use the light theme and the dark theme.
      
Part 2: Parenthesis Support
---
 
```
//Nathaniel Chandler, CIS 7, 9/5/18
#include <iostream>
#include <string>
#include <vector>
using namespace std;

bool isFunction(string input);

int main()
{
	bool done = false;
	while (!done)
	{
		vector<bool> statement;
		string input;
		cout << "Enter a Function:" << endl;
		getline(cin, input);

		if (isFunction(input))
		{
			cout << "This is a well formed function" << endl;
		}
		else
		{
			cout << "This is not a well formed function" << endl;
		}
		cout << "Would you like to run again? (y/n)" << endl;

		cin >> input;
		cin.ignore();

		if (input == "y" || input == "Y")
		{
			done = false;
		}
		else
		{
			done = true;
		}
	}
	system("pause");
	return 0;
}

bool isFunction(string input)
{
	string connectors = "&^vV";
	string negation = "!`~";
	string ifElse = "->";
	char previous = '*';

	// Bookend Checks
	for (int i = 0; i < input.length(); i++) //parse through front
	{
		if (input[i] == ' ' || input[i] == '(' || negation.find(input[i]) != std::string::npos) //not operation or negation, skip
		{
			continue;
		}
		else if (isalpha(input[i])) // if var, break, else false
		{
			break;
		}
		else
		{
			return false;
		}
	}

	for (int i = input.length() - 1; i > 0; i--) // parse through back
	{
		if (input[i] == ' ' || input[i] == ')') // not operation, skip
		{
			continue;
		}
		else if (isalpha(input[i])) // if var, break,else false
		{
			break;
		}
		else
		{
			return false;
		}
	}

	//Parenthesis check
	int openP = 0;
	int closeP = 0;
	for (int i = 0; i < input.length(); i++)
	{
		if (input[i] == ' ') //if space, skip
		{
			continue;
		}
		else if (input[i] == '(') // if open Par, check
		{
			openP++;
			if (!isalpha(input[i + 1]) && input[i + 1] != '(') //if next not var or open Par, break
			{
				return false;
			}
		}
		else if (input[i] == ')') // if close par, check
		{
			closeP++;
			if (!isalpha(input[i - 1]) && input[i - 1] != ')') // if prev not var or close par, break
			{
				return false;
			}
		}
	}
	if (openP != closeP) // every open has a close
	{
		return false;
	}


	//Logic
	for (char element : input)
	{
		if (element == ' ') //if space, skip
		{
			continue;
		}
		else if (connectors.find(element) != std::string::npos) // if connector(not ifelse)
		{
			if (connectors.find(previous) != std::string::npos) // if prev was connector, break
			{
				return false;
			}
		}
		else if (ifElse.find(element) != std::string::npos) // if ifElse
		{
			if (connectors.find(previous) != std::string::npos || previous == ifElse[1]) // if prev was connector or '>', break
			{
				return false;
			}
			if (previous == element) // if repeat char, break
			{
				return false;
			}
		}
		else if (negation.find(element) != std::string::npos) // if Not
		{
			if (negation.find(previous) != std::string::npos || isalpha(previous)) //if repeat or prev letter, break
			{
				return false;
			}
		}
		else if (isalpha(element)) // if Char
		{
			if (isalpha(previous) && connectors.find(previous) == std::string::npos) // if prev was char and not v, break
			{
				return false;
			}
		}

		previous = element;
	}

	return true;
}
```
