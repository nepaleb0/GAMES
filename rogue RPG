#include <iostream>
#include <string>
#include <cstdlib>
#include <ctime>
#include <stdlib.h>
using namespace std;

void ClearConsole(){
    for(int i = 0; i < 100; i ++){
        cout <<"\n";
    }
}

int main()
{
    srand(static_cast<unsigned int>(time(0)));
    
    class Mob{
    public:
        int health;
        int attack;
        int score;
    };
    
    class Character{
    public:
        int health = 100;
        int attack = 10;
        int score = 0;
    };
    
    class Item{
    public:
        int health;
        int attack;
        int score;
    };
    
    class Shop{
    public:
        int price;
        int item;
    };
    
    class Boss{
    public:
        int health;
        int attack;
        int score;
    };
    
    Boss Warwor{250, 15, 100};
    
    Shop HealinPpotion{20, 5};
    Shop NewSword{15, 5};
    
    Character gamer{};
    
    Mob Slime{50, 5, 10};
    Mob Ant{1, 0, 1};
    
    cout <<"Main menu\n\nStart - 1\nQuit - 0"<<endl;

    cout <<"\nEnter your choise: ";
    int MenuInput;
    cin >>MenuInput;

    if (MenuInput == 0){
        return 0;
    }
    
    cout <<"Enter nickname: ";
    string nickname;
    cin >>nickname;
    
    ClearConsole();
    
    int Difficulty = 0;
    
    while (MenuInput != 0){
        Difficulty++;
        int MobID;
        
        int fight = 0;
        if (fight == 0){
            MobID = rand() % 3;
            fight = 1;
        }
        
        Mob MobNow {};
        
        switch (MobID) {
            case 0:
                MobNow = Slime;
                break;
                
            case 1:
                MobNow = Ant;
                break;
                
            case 2:
                if (rand()%100 < 10){
                    MobNow.attack = Warwor.attack;
                    MobNow.health = Warwor.health;
                    MobNow.score = Warwor.score;
                }
                break;
        }
        MobNow.health = MobNow.health + (Difficulty*2);
        MobNow.attack = MobNow.attack + (Difficulty);
        
        while (MenuInput != 0){
            int item = rand()%3;
            
            cout <<nickname<<"\t\t\t";
            switch (MobID) {
                case 0:
                    cout <<"Slime";
                    break;
                    
                case 1:
                    cout <<"Ant";
                    break;
                    
                case 2:
                    cout <<"[BOSS] WARWOR";
                    break;
            }
            cout <<"\nHealth: "<<gamer.health<<"\t\t\t"<<MobNow.health<<endl;
            cout <<"Attack: "<<gamer.attack<<"\t\t\t"<<MobNow.attack<<endl;
            cout <<"Score: "<<gamer.score<<endl;
            
            cout <<"\nAttack - 1\nRun - 2 (you can run if chance higher than 50)\nEnter Shop - 3\nChoice: ";
            cin >>MenuInput;
            
            
            if (MenuInput == 2){
                int RunChance = rand()%100;
                if (RunChance > 50){
                    MenuInput = 0;
                }else{
                    gamer.health = gamer.health - MobNow.attack;
                }
            }else if (MenuInput == 1){
                MobNow.health = MobNow.health - gamer.attack;
                if (MobNow.health <= 0){
                    gamer.score = gamer.score + MobNow.score;
                    MenuInput = 0;
                    cout <<"\n";
                    switch (item) {
                        case 0:
                            cout <<"You found healing potion (+ 10 health)";
                            gamer.health = gamer.health + 10;
                            break;
                        case 1:
                            cout <<"You found New sword (+5 attack)";
                            gamer.attack = gamer.attack + 5;
                            break;
                        case 2:
                            cout <<"You found some coins on the ground";
                            gamer.score = gamer.score + rand ()%10;
                    }
                    cout <<"\nenter something and press enter\n";
                    string IDontKnowHowToNameThis;
                    cin >>IDontKnowHowToNameThis;
                }else{
                    gamer.health = gamer.health - MobNow.attack;
                }
            }else if (MenuInput == 3){
                ClearConsole();
                cout <<"Your score: "<<gamer.score<<endl;
                cout <<"New Sword (-15 score / +5 attack) - 1\nHealing potion(-20 score/ + 10 Health) - 2"<<endl;
                int ShopList;
                cin >>ShopList;
                if (ShopList == 1){
                    gamer.attack = gamer.attack + NewSword.item;
                    gamer.score = gamer.score - NewSword.price;
                }else if (ShopList == 2){
                    gamer.health = gamer.health + HealinPpotion.item;
                    gamer.score = gamer.score - HealinPpotion.price;
                }
            }
            
            ClearConsole();
        }
        if (gamer.health > 0){
            MenuInput = 1;
        }else{
            MenuInput = 0;
            cout <<"You failed...\nSCORE = "<<gamer.score<<endl;
        }
    }
}
