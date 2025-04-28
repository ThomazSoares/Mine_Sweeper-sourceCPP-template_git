# Mine_Sweeper-sourceCPP-template_git
{

    #include <iostream>
    #include <ctime>
    #include <cstdlib>
    
    using namespace std;
    
    int main(){
        //basis
        srand(time(0));
    
        //introduction
        int size = 16;
        int grid[size][size];
    
        //bomb gen (t1)
        int num_rand1;
    
        for (int i = 0; i < size; i++){
            for (int j = 0; j < size; j++){
                num_rand1 = (rand() % 10) + 1; // 1 - 10
    
                if (num_rand1 <= 4){
                    grid[i][j] = 1;
                } else{
                    grid[i][j] = 0;
                }
            }
        }
    
        //bomb gen (t2)
        int num_rand2;
        int bomb_s1;
    
        for (int i = 1; i < size - 1; i++){
            for (int j = 1; j < size - 1; j++){
                bomb_s1 = 0;
    
                if (grid[i][j] == 0 || grid[i][j] == 1){
                    for (int i1 = i - 1; i1 < i + 2; i1++){
                        for (int j1 = j - 1; j1 < j + 2; j1++){
                            if (grid[i1][j1] == 1 || grid[i1][j1] == 2 || grid[i1][j1] == 3 && i1 != i && j1 != j){
                                bomb_s1++;
                            }
                        }
                    }
    
                    if (8 - bomb_s1 >= 6){
                        grid[i][j] = 2;
    
                        for (int i1 = i - 1; i1 < i + 2; i1++){
                            for (int j1 = j - 1; j1 < j + 2; j1++){
                                num_rand2 = (rand() % 10) + 1; // 1 - 10
    
                                if (num_rand2 <= 4 && grid[i1][j1] == 0 && i1 != i && j1 != j){
                                    grid[i1][j1] = 3;
                                }
                            }
                        }
                    }
                }
            }
        }
    
        //bomb gen (t3)
        int num_rand3;
    
        for (int i = 1; i < size - 1; i++){
            if (grid[i - 1][0] == 0 && grid[i - 1][1] == 0 && grid[i][0] == 0 && grid[i][1] == 0 && grid[i + 1][0] == 0 && grid[i + 1][1] == 0){
                grid[i][0] = 4;
    
                num_rand3 = (rand() % 5) + 1;
    
                switch(num_rand3){
                    case 1:
                        grid[i - 1][0] = 5;
                        break;
                    case 2:
                        grid[i - 1][1] = 5;
                        break;
                    case 3:
                        grid[i][1] = 5;
                        break;
                    case 4:
                        grid[i + 1][0] = 5;
                        break;
                    case 5:
                        grid[i + 1][1] = 5;
                        break;
                }
            }
        }
        for (int i = 1; i < size - 1; i++){
            if (grid[i - 1][size - 2] == 0 && grid[i - 1][size - 1] == 0 && grid[i][size - 2] == 0 && grid[i][size - 1] == 0 && grid[i + 1][size - 2] == 0 && grid[i + 1][size - 1] == 0){
                grid[i][size - 1] = 4;
    
                num_rand3 = (rand() % 5) + 1;
    
                switch(num_rand3){
                    case 1:
                        grid[i - 1][size - 2] = 5;
                        break;
                    case 2:
                        grid[i - 1][size - 1] = 5;
                        break;
                    case 3:
                        grid[i][size - 2] = 5;
                        break;
                    case 4:
                        grid[i + 1][size - 2] = 5;
                        break;
                    case 5:
                        grid[i + 1][size - 1] = 5;
                        break;
                }
            }
        }
        for (int j = 1; j < size - 1; j++){
            if (grid[0][j - 1] == 0 && grid[0][j] == 0 && grid[0][j + 1] == 0 && grid[1][j - 1] == 0 && grid[1][j] == 0 && grid[1][j + 1] == 0){
                grid[0][j] = 4;
    
                num_rand3 = (rand() % 5) + 1;
    
                switch(num_rand3){
                    case 1:
                        grid[0][j - 1] = 5;
                        break;
                    case 2:
                        grid[0][j + 1] = 5;
                        break;
                    case 3:
                        grid[1][j - 1] = 5;
                        break;
                    case 4:
                        grid[1][j] = 5;
                        break;
                    case 5:
                        grid[1][j + 1] = 5;
                        break;
                }
            }
        }
        for (int j = 1; j < size - 1; j++){
            if (grid[size - 2][j - 1] == 0 && grid[size - 2][j] == 0 && grid[size - 2][j + 1] == 0 && grid[size - 1][j - 1] == 0 && grid[size - 1][j] == 0 && grid[size - 1][j + 1] == 0){
                grid[size - 1][j] = 4;
    
                num_rand3 = (rand() % 5) + 1;
    
                switch(num_rand3){
                    case 1:
                        grid[size - 2][j - 1] = 5;
                        break;
                    case 2:
                        grid[size - 2][j] = 5;
                        break;
                    case 3:
                        grid[size - 2][j + 1] = 5;
                        break;
                    case 4:
                        grid[size - 1][j - 1] = 5;
                        break;
                    case 5:
                        grid[size - 1][j + 1] = 5;
                        break;
                }
            }
        }
    
        //bomb gen (t4)
        int num_rand4;
    
        if (grid[0][0] == 0 && grid[0][1] == 0 && grid[1][0] == 0 && grid[1][1] == 0){
            grid[0][0] = 6;
    
            num_rand4 = (rand() % 3) + 1;
    
            switch(num_rand4){
                case 1:
                    grid[0][1] = 7;
                    break;
                case 2:
                    grid[1][0] = 7;
                    break;
                case 3:
                    grid[1][1] = 7;
                    break;
            }
        } else if (grid[0][size - 2] == 0 && grid[0][size - 1] == 0 && grid[1][size - 2] == 0 && grid[1][size - 1] == 0){
            grid[0][size - 1] = 6;
    
            num_rand4 = (rand() % 3) + 1;
    
            switch(num_rand4){
                case 1:
                    grid[0][size - 2] = 7;
                    break;
                case 2:
                    grid[1][size - 2] = 7;
                    break;
                case 3:
                    grid[1][size - 1] = 7;
                    break;
            }
        } else if (grid[size - 2][0] == 0 && grid[size - 2][1] == 0 && grid[size - 1][0] == 0 && grid[size - 1][1] == 0){
            grid[size - 1][0] = 6;
    
            num_rand4 = (rand() % 3) + 1;
    
            switch(num_rand4){
                case 1:
                    grid[size - 2][0] = 7;
                    break;
                case 2:
                    grid[size - 2][1] = 7;
                    break;
                case 3:
                    grid[size - 1][1] = 7;
                    break;
            }
        } else if (grid[size - 2][size - 2] == 0 && grid[size - 2][size - 1] == 0 && grid[size - 1][size - 2] == 0 && grid[size - 1][size - 1] == 0){
            grid[size - 1][size - 1] = 6;
    
            num_rand4 = (rand() % 3) + 1;
    
            switch(num_rand4){
                case 1:
                    grid[size - 2][size - 2] = 7;
                    break;
                case 2:
                    grid[size - 2][size - 1] = 7;
                    break;
                case 3:
                    grid[size - 1][size - 2] = 7;
                    break;
            }
        }
    
        //print grid
        for (int i = 0; i < size; i++){
            for (int j = 0; j < size; j++){
                if (j != size - 1){
                    cout << grid[i][j] << "  ";
                } else{
                    cout << grid[i][j] << "\n";
                }
            }
        }
    
        //count
        int s0 = 0, s1 = 0, s2 = 0, s3 = 0, s4 = 0, s5 = 0, s6 = 0, s7 = 0;
    
        for (int i = 0; i < size; i++){
            for (int j = 0; j < size; j++){
                if (grid[i][j] == 0){
                    s0++;
                } else if (grid[i][j] == 1){
                    s1++;
                } else if (grid[i][j] == 2){
                    s2++;
                } else if (grid[i][j] == 3){
                    s3++;
                } else if (grid[i][j] == 4){
                    s4++;
                } else if (grid[i][j] == 5){
                    s5++;
                } else if (grid[i][j] == 6){
                    s6++;
                } else{
                    s7++;
                }
            }
        }
    
        cout << "\n";
        cout << s0 << " " << s1 << " " << s2 << " " << s3 << " " << s4 << " " << s5 << " " << s6 << " " << s7 << "\n";
    
        return 0;
    }
}
