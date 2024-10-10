# Convertire il l'orologio da AM / PM a 24H 

```c
char* timeConversion(char* s) {
    // Extract hours, minutes, seconds, and AM/PM indicator from the input string
    int hours, minutes, seconds;
    char am_pm[3];
    //sscanf pareses data from a provided string instead of stdin 
    sscanf(s, "%d:%d:%d%s", &hours, &minutes, &seconds, am_pm);

    // Adjust hours based on the AM/PM indicator
    if (strcmp(am_pm, "PM") == 0 && hours != 12) {
        hours += 12;
    } else if (strcmp(am_pm, "AM") == 0 && hours == 12) {
        hours = 0;
    }

    // Allocate memory for the result string
    char* result = (char*)malloc(9);
    
    // Format the result string in 24-hour clock format
    sprintf(result, "%02d:%02d:%02d", hours, minutes, seconds);

    return result;
}

```

questa qui è una funzione che riceve la stringa di tempo in input e restituisce il tempo nel formato militare aka 24H 