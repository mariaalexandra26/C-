# Joc-x-si-0---C-

#include <iostream>
using namespace std;
char matrice[3][3] = {{'1', '2', '3'},
                    {'4', '5', '6'},
                    {'7', '8', '9'}};

void afisare_matrice()
{
    cout << "Jucatorul 1 [X]  -  Jucatorul 2 [O]\n\n";
    cout << "     |     |     \n";
    for (int i = 0; i < 3; i++) 
    {
        cout << "  " << matrice[i][0] << "  |  " << matrice[i][1] << "  |  " << matrice[i][2] << "  \n";
        if (i != 2) cout << "_____|_____|_____\n";
    }
    cout << "     |     |     \n\n";
}

bool verifica_castig()
{
    int i;
    for(i=0; i<3; i++)
    {
        if ( matrice[i][0] == matrice[i][1] && matrice[i][1] == matrice[i][2] )
            return true;
        if ( matrice[0][i] == matrice[1][i] && matrice[1][i] == matrice[2][i] )
            return true;
    }
    if ( matrice[0][0] == matrice[1][1] && matrice[1][1] == matrice[2][2])
        return true;
    if ( matrice[0][2] == matrice[1][1] && matrice[1][1] == matrice[2][0])
        return true;
    return false;
}

bool verifica_egalitate()
{
    int i, j;
    for (i=0; i<3; i++)
    for (j=0; j<3; j++)
        if ( matrice[i][j] != 'x' && matrice[i][j] != '0')
            return false;
    return true;
}

int main()
{
    int jucator = 1, i, j, semn, a;
    
    do
    {
        afisare_matrice();
        jucator = (jucator %  2)? 1 : 2;
        semn = (jucator == 1)? 'x' : '0';

        cout<<"Jucator "<<jucator<<", alege un numar intre 1 si 9:";
        cin>>a;
        i=(a-1)/3;
        j=(a-1)%3;
        if (matrice[i][j] == 'x' || matrice [i][j] == '0')
            cout<<"Spatiu deja ocupat!";
        else
            matrice[i][j] = semn;
        if (verifica_castig())
        {
            afisare_matrice();
            cout<<"Jucatorul "<<jucator<<" a castigat! Felicitari!";
            break;
        }
        else if( verifica_egalitate() )
        {
            afisare_matrice();
            cout<<"Egalitate!";
            break;
        }
        jucator++;
    }while(true);
}
