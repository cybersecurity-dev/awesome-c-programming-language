# [Enumarations](https://cppreference.com/w/c/language/enum.html)

* `Basic Enum` Example
    ```c
    enum Day {
        MONDAY,
        TUESDAY,
        WEDNESDAY,
        THURSDAY,
        FRIDAY,
        SATURDAY,
        SUNDAY
    };
    
    int main() {
        enum Day today = SATURDAY;
        printf("Today is day number: %d\n", today);
        return 0;
    }
    ```
* Enum with `Custom Values`
    ```c
    enum ErrorCode {
        OK = 0,
        WARNING = 1,
        ERROR = 5,
        CRITICAL = 10,
        NOT_FOUND = 404
    };
    
    int main() {
        enum ErrorCode status = NOT_FOUND;
        printf("Status code: %d\n", status);
        return 0;
    }
    ```
* Using Enum in a `switch`
    ```c
    enum TrafficLight {
        RED,
        YELLOW,
        GREEN
    };
    
    int main() {
        enum TrafficLight light = GREEN;
    
        switch (light) {
            case RED:
                printf("Stop!\n");
                break;
            case YELLOW:
                printf("Get Ready!\n");
                break;
            case GREEN:
                printf("Go!\n");
                break;
        }
    
        return 0;
    }
    ```