### Материалы для тестирования

[Номера карт](https://docs.google.com/document/d/1Szm33_53LqAecQUNGqLYmjHRV3NudmnHytCcYYtu3EM/edit?usp=sharing)

[Домашнее задание](https://github.com/netology-code/javaqa-homeworks/tree/master/intro)

### Шаги для воспроизведения

- Открыть IDEA

- Завести новый проект

- Создать ClassMain

### Переменная

<pre><code> public class Main {
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
} </code></pre>


- Запустить метод Ctrl+Shift+F10

### Результат

Ожидаемый:
Все номера валидные

Фактический:
Не все номера валидные 

### Cкриншот ошибки
[Скриншот](https://docs.google.com/document/d/1VsQUgqRYvijTpx083E-BevNdSPWf-4Pyk9wP1_8lhtA/edit?usp=sharing)

### Окружение

Windows 10
Java version "11.0.9.1"
IntelliJ IDEA Community Edition 2020.3.1