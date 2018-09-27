#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <malloc.h>
#include <ctype.h>
#include <string.h>

struct values {
    double x_values[200];
    double y_values[200];
    double y_val[200];
    int m;
} function_G, function_F, function_Y;

int main() {

    int j = 0, i = 0, tf = 0;
    double G, F, Y, y = 0,r, y2 = 0, y_from_fail, x, size_step, max_x = 0, min_x = 0, max_y = 0, min_y = 0;
    char l[255];
    char X[255];
    char _x_[255];
    char _y_[255];
    char org[510];
    char dst[255];
    double distance_dst, difference, dst_and_dif;
    char *string;
    printf("Введите начальную границу X = ");
    scanf("%s", &l);
    x = atof(l);
    printf("Введите конечную границу X1 = ");
    scanf("%s", &l);
    double x1 = atof(l);
    printf("Введите A = ");
    scanf("%s", &l);
    double a = atof(l);
    printf("Введите размер шага = ");
    scanf("%s", &l);
    r = atof(l);
    FILE *v;
    v = fopen("/home/argo/ClionProjects/Laba7/text.txt", "w+");

    while (x <x1) {
        if ((5 * pow(a, 2) - 9 * a * x + 4 * pow(x, 2)) != 0) {
            G = (5 * (-10 * pow(a, 2) + 27 * a * x + 28 * pow(x, 2))) /
                (5 * pow(a, 2) - 9 * a * x + 4 * pow(x, 2));
            if (j == 0) {
                printf("╔═════════╦═════════╗\n");
                printf("║    X    ║    Y    ║\n");
                printf("╠═════════╬═════════╣\n");
                function_G.x_values[j] = x;
                function_G.y_values[j] = G;
                printf("║%9.3lf║%9.3lf║\n", function_G.x_values[j], function_G.y_values[j]);
            }
            if (j >= 1) {
                function_G.x_values[j] = x;
                function_G.y_values[j] = G;
                printf("║%9.3lf║%9.3lf║\n", function_G.x_values[j], function_G.y_values[j]);
            }
            if (j == 1)
                y = (function_G.x_values[j] + function_G.y_values[j]) / 2;
            else if (j > 1) {
                y2 = (function_G.x_values[j] + function_G.y_values[j]) / 2;
            }
            if ((fabs(y) > 1.2 * fabs(y2)) && (j > 1) && (y2 != 0)) {
                x += (r*2);
                y = y2;
            } else {
                if ((fabs(y) < 1.2 * fabs(y2)) && (j > 1) && (y2 != 0)) {
                    x += (r/2);
                    y = y2;
                } else x += r;
                if (j > 1) {
                    y = y2;
                }

            }

            j += 1;

            continue;
        } else
            printf("%s\n",
                   "G не может быть результатом деления на 0. Введите другие значения переменных.");
        break;

    }
    if (j != 0) {
        if (function_G.m != j)
            function_G.m = j;

        for (j = 0; j < function_G.m; j++) {
            if (j == 0) {
                max_x = function_G.x_values[j];
                min_x = function_G.x_values[j];
                max_y = function_G.y_values[j];
                min_y = function_G.y_values[j];
            }
            if (max_x < function_G.x_values[j])
                max_x = function_G.x_values[j];
            if (min_x > function_G.x_values[j])
                min_x = function_G.x_values[j];
            if (max_y < function_G.y_values[j])
                max_y = function_G.y_values[j];
            if (min_y > function_G.y_values[j])
                min_y = function_G.y_values[j];
        }
        printf("╚═════════╩═════════╝\n");
        printf("╔════════════════════════╦══════════╗\n");
        printf("║Максимальное значение Х:║%10.3lf║\n", max_x);
        printf("╠════════════════════════╬══════════╣\n");
        printf("║Минимальное значение Х: ║%10.3lf║\n", min_x);
        printf("╠════════════════════════╬══════════╣\n");
        printf("║Максимальное значение Y:║%10.3lf║\n", max_y);
        printf("╠════════════════════════╬══════════╣\n");
        printf("║Минимальное значение Y: ║%10.3lf║\n", min_y);
        printf("╚════════════════════════╩══════════╝\n");

        memset(org, 0, 255);
        memset(_x_, 0, 255);
        memset(_y_, 0, 255);

        for (j = 0; j < function_G.m; j++) {
            sprintf(_x_, "%.2lf ", function_G.x_values[j]);
            sprintf(_y_, "%.2lf ", function_G.y_values[j]);
            strcat(org, _x_);
            strcat(org, _y_);
        }
        printf("%s\n", org);


        printf("Введите шаблон для поиска:");
        scanf("%s", dst);

        string = strstr(org, dst);
        if (string != NULL) {
            while (string != NULL) {

                string = strstr(org, dst); /* нашли совпадение, если нет то нулл*/
                distance_dst = strlen(dst); /* находим длину строки-шаблона*/
                difference = string -
                             org;/*находим разницу между длинами количеством знаков в оставшейся строке и оригинальной */
                dst_and_dif = distance_dst + difference; /* сумма длин строки-шаблона и разницы*/
                for (j = 0; j <= dst_and_dif; ++j) {
                    memset(org, '_', j);

                    if (j == dst_and_dif) {
                        /*printf("Сам массив:%s\n Количество символов(длина) в строке-шаблоне:%.0lf\n Разница индексов(длина):%.0lf\n Сумма длин:%.0lf\n",
                               org, distance_dst, difference, dst_and_dif);*/
                        i += 1;
                    }
                }
            }
            printf("Количество найденных совпадений:%i\n", i);
        } else
            printf("Строка не найдена\n");
        j = 0;
    }
    x = function_G.x_values[0];
    while (x<x1) {
        F = sin(28 * pow(a, 2) - 57 * a * x + 14 * pow(x, 2));
        if (j == 0) {
            printf("╔═════════╦═════════╗\n");
            printf("║    X    ║    Y    ║\n");
            printf("╠═════════╬═════════╣\n");
            function_F.x_values[j] = x;
            function_F.y_values[j] = F;
            printf("║%9.3lf║%9.3lf║\n", function_F.x_values[j], function_F.y_values[j]);
        }
        if (j >= 1) {
            function_F.x_values[j] = x;
            function_F.y_values[j] = F;
            printf("║%9.3lf║%9.3lf║\n", function_F.x_values[j], function_F.y_values[j]);
        }
        if (j == 1)
            y = (function_F.x_values[j] + function_F.y_values[j]) / 2;
        else if (j > 1) {
            y2 = (function_F.x_values[j] + function_F.y_values[j]) / 2;
        }
        if ((fabs(y) > 1.2 * fabs(y2)) && (j > 1) && (y2 != 0)) {
            x += (r*2);
            y = y2;
        } else {
            if ((fabs(y) < 1.2 * fabs(y2)) && (j > 1) && (y2 != 0)) {
                x += (r/2);
                y = y2;
            } else x += r;
            if (j > 1) {
                y = y2;
            }

        }

        j += 1;
        continue;

    }
    if (j != 0) {
        if (function_F.m != j)
            function_F.m = j;
        for (j = 0; j < function_F.m; j++) {
            if (j == 0) {
                max_x = function_F.x_values[j];
                min_x = function_F.x_values[j];
                max_y = function_F.y_values[j];
                min_y = function_F.y_values[j];
            }
            if (max_x < function_F.x_values[j])
                max_x = function_F.x_values[j];
            if (min_x > function_F.x_values[j])
                min_x = function_F.x_values[j];
            if (max_y < function_F.y_values[j])
                max_y = function_F.y_values[j];
            if (min_y > function_F.y_values[j])
                min_y = function_F.y_values[j];
        }
        printf("╚═════════╩═════════╝\n");
        printf("╔════════════════════════╦══════════╗\n");
        printf("║Максимальное значение Х:║%10.3lf║\n", max_x);
        printf("╠════════════════════════╬══════════╣\n");
        printf("║Минимальное значение Х: ║%10.3lf║\n", min_x);
        printf("╠════════════════════════╬══════════╣\n");
        printf("║Максимальное значение Y:║%10.3lf║\n", max_y);
        printf("╠════════════════════════╬══════════╣\n");
        printf("║Минимальное значение Y: ║%10.3lf║\n", min_y);
        printf("╚════════════════════════╩══════════╝\n");


        memset(org, 0, 255);
        memset(_x_, 0, 255);
        memset(_y_, 0, 255);

        for (j = 0; j < function_F.m; j++) {
            sprintf(_x_, "%.3lf ", function_F.x_values[j]);
            sprintf(_y_, "%.3lf ", function_F.y_values[j]);
            strcat(org, _x_);
            strcat(org, _y_);

        }
        printf("%s\n", org);


        printf("Введите шаблон для поиска:");
        scanf("%s", dst);


        string = strstr(org, dst);
        if (string != NULL) {
            while (string != NULL) {
                string = strstr(org, dst);
                distance_dst = strlen(dst);
                difference = string -
                             org;
                dst_and_dif = distance_dst + difference;
                for (j = 0; j <= dst_and_dif; ++j) {
                    memset(org, '_', j);
                    if (j == dst_and_dif) {
                        /*printf("Сам массив:%s\n Количество символов(длина) в строке-шаблоне:%.0lf\n Разница индексов(длина):%.0lf\n Сумма длин:%.0lf\n",
                               org, distance_dst, difference, dst_and_dif);*/
                        i += 1;
                    }
                }
            }
            printf("Количество найденных совпадений:%i\n", i);
        } else
            printf("Строка не найдена\n");
        j = 0;
    }
    x = function_G.x_values[0];
    while (x<x1) {
        Y = log(-27 * pow(a, 2) + 24 * a * x + 35 * pow(x, 2) + 1);
        if (Y > 0) {

            if (j == 0) {
                printf("╔═════════╦═════════╗\n");
                printf("║    X    ║    Y    ║\n");
                printf("╠═════════╬═════════╣\n");
                function_Y.x_values[j] = x;
                function_Y.y_values[j] = Y;
                printf("║%9.3lf║%9.3lf║\n", function_Y.x_values[j], function_Y.y_values[j]);
            }
            if (j >= 1) {
                function_Y.x_values[j] = x;
                function_Y.y_values[j] = Y;
                printf("║%9.3lf║%9.3lf║\n", function_Y.x_values[j], function_Y.y_values[j]);
            }
            if (j == 1)
                y = (function_Y.x_values[j] + function_Y.y_values[j]) / 2;
            else if (j > 1) {
                y2 = (function_Y.x_values[j] + function_Y.y_values[j]) / 2;
            }
            if ((fabs(y) > 1.2 * fabs(y2)) && (j > 1) && (y2 != 0)) {
                x += (r*2);
                y = y2;
            } else {
                if ((fabs(y) < 1.2 * fabs(y2)) && (j > 1) && (y2 != 0)) {
                    x += (r/2);
                    y = y2;
                } else x += r;
                if (j > 1) {
                    y = y2;
                }

            }

            j += 1;

            continue;
        } else
            printf("%s\n",
                   "Логарифм Y не может быть найден при таких значениях");
        break;

    }
    if (j != 0) {
        if (function_Y.m != j)
            function_Y.m = j;
        for (j = 0; j < function_Y.m; j++) {
            if (j == 0) {
                max_x = function_Y.x_values[j];
                min_x = function_Y.x_values[j];
                max_y = function_Y.y_values[j];
                min_y = function_Y.y_values[j];
            }
            if (max_x < function_Y.x_values[j])
                max_x = function_Y.x_values[j];
            if (min_x > function_Y.x_values[j])
                min_x = function_Y.x_values[j];
            if (max_y < function_Y.y_values[j])
                max_y = function_Y.y_values[j];
            if (min_y > function_Y.y_values[j])
                min_y = function_Y.y_values[j];
        }
        printf("╚═════════╩═════════╝\n");
        printf("╔════════════════════════╦══════════╗\n");
        printf("║Максимальное значение Х:║%10.3lf║\n", max_x);
        printf("╠════════════════════════╬══════════╣\n");
        printf("║Минимальное значение Х: ║%10.3lf║\n", min_x);
        printf("╠════════════════════════╬══════════╣\n");
        printf("║Максимальное значение Y:║%10.3lf║\n", max_y);
        printf("╠════════════════════════╬══════════╣\n");
        printf("║Минимальное значение Y: ║%10.3lf║\n", min_y);
        printf("╚════════════════════════╩══════════╝\n");


        memset(org, 0, 255);
        memset(_x_, 0, 255);
        memset(_y_, 0, 255);

        for (j = 0; j < function_Y.m; j++) {
            sprintf(_x_, "%.3lf ", function_Y.x_values[j]);
            sprintf(_y_, "%.3lf ", function_Y.y_values[j]);
            strcat(org, _x_);
            strcat(org, _y_);

        }
        printf("%s\n", org);


        printf("Введите шаблон для поиска:");
        scanf("%s", dst);


        string = strstr(org, dst);
        if (string != NULL) {
            while (string != NULL) {
                string = strstr(org, dst);
                distance_dst = strlen(dst);
                difference = string -
                             org;
                dst_and_dif = distance_dst + difference;
                for (j = 0; j <= dst_and_dif; ++j) {
                    memset(org, '_', j);
                    if (j == dst_and_dif) {
                        /*printf("Сам массив:%s\n Количество символов(длина) в строке-шаблоне:%.0lf\n Разница индексов(длина):%.0lf\n Сумма длин:%.0lf\n",
                               org, distance_dst, difference, dst_and_dif);*/
                        i += 1;
                    }
                }
            }
            printf("Количество найденных совпадений:%i\n", i);
        } else
            printf("Строка не найдена\n");
    }
    if (function_G.m != 0) {
        for (i = 0; i < function_G.m; ++i) {
            fprintf(v, "%f\n", function_G.y_values[i]);
        }
    }
    function_F.m = function_F.m + function_G.m;
    if (function_F.m > function_G.m) {
        for (i = 0; i < function_F.m; ++i) {
            fprintf(v, "%f\n", function_F.y_values[i]);
        }
    }
    function_Y.m = function_F.m + function_Y.m;
    if (function_Y.m > function_F.m) {
        for (i = 0; i < function_Y.m; ++i) {
            fprintf(v, "%f\n", function_Y.y_values[i]);
        }
    }
    fclose(v);
    v = fopen("/home/argo/ClionProjects/Laba7/text.txt", "r");
    if (function_G.m != 0) {
        memset(function_G.y_values, 0, 200);
        for (i = 0; i < function_G.m; ++i) {
            fscanf(v, "%lf\n", &y_from_fail);
            function_G.y_values[i] = y_from_fail;
            printf("%.3lf;", function_G.y_values[i]);
        }
    }
    if (function_F.m > function_G.m) {
        memset(function_F.y_values, 0, 200);
        for (i = 0; i < function_F.m; ++i) {
            fscanf(v, "%lf\n", &y_from_fail);
            function_F.y_values[i] = y_from_fail;
            printf("%lf;", function_F.y_values[i]);
        }
    }
    if (function_Y.m > function_F.m) {
        memset(function_F.y_values, 0, 200);
        for (i = 0; i < function_F.m; ++i) {
            fscanf(v, "%lf\n", &y_from_fail);
            function_F.y_values[i] = y_from_fail;
            printf("%lf;", function_F.y_values[i]);
        }
    }
    fclose(v);

    return 0;
}
