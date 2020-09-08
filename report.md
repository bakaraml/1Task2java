# Отчёт о тестировании Credit Card Number Validator

## Краткое описание

08.09.2020 - 08.09.2020 было проведено ручное тестирование приложения Credit Card Number Validator.

На тестирование затрачено: 1 час

В результате тестирования дефекты не выявлены

## Описание процесса тестирования

В процессе тестирования использовались следующие артефакты:
* Руководство по установке IntelliJ IDEA
* код программиста 

```
public class Main {
  public static void main(String[] args) {
    // TODO: подставлять номер карты нужно сюда между двойными кавычками, без пробелов
    String number = "5351719427810741";
    System.out.println(String.format("Result is %s", isValidCardNumber(number) ? "OK" : "FAIL"));
  }

  public static boolean isValidCardNumber(String number) {
    if (number == null) {
      return false;
    }

    if (number.length() != 16) {
      return false;
    }

    long result = 0;
    for (int i = 0; i < number.length(); i++) {
      int digit;
      try {
        digit = Integer.parseInt(number.charAt(i) + "");
      } catch (NumberFormatException e) {
        return false;
      }

      if (i % 2 == 0) {
        digit *= 2;
        if (digit > 9) {
          digit -= 9;
        }
      }
      result += digit;
    }

    return (result != 0) && (result % 10 == 0);
  }
}
```

В качестве тестовых данных использовались данные с сайта https://fakepersongenerator.com/Random1/credit_card_generator
* 5504590361258791 ОК
* 4118587321622968 ОК
* 4016751102899491 ОК
* 5128008714951042 ОК
* 4537508181959970 ОК
* 4547149422966686 OK
* 4090217834281530 OK
* 4039560878365626 ОК
* 4067387062944114 OK
* 6011245582964183084 FAIL
* 36598779881714 FAIL

Тестирование производилось в следующем окружении:
* macOS Catalina 10.15.6 x64 
* java 11.0.8
* IntelliJ IDEA