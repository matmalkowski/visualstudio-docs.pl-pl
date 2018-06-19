---
title: Informacje o oknie rejestrów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, about Registers window
- debugging [Visual Studio], Registers window
ms.assetid: ab354047-053e-4f94-8ac1-26e761442b6f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 37b2c34971750d8e6db0173f6034342b9efbfd97
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474417"
---
# <a name="about-the-registers-window-in-visual-studio"></a>Informacje o oknie rejestrów w programie Visual Studio
**Rejestruje** okno jest dostępne tylko wtedy, gdy w włączone jest debugowanie poziomie adresu **opcje** okno dialogowe **debugowanie** węzła.  
  
 Rejestry są specjalne lokalizacje w procesora (CPU), które są używane do przechowywania małych fragmentów danych, który procesor jest aktywnie nad. Kompilowanie lub interpretowanie kodu źródłowego generuje instrukcje dotyczące przenoszenia danych z pamięci do rejestrów i z powrotem ponownie, zgodnie z potrzebami. Uzyskiwanie dostępu do danych w rejestrach jest bardzo szybko w porównaniu do uzyskiwania dostępu do danych w pamięci, więc zwykle wykonać szybciej niż przy użyciu kodu, który wymaga procesora do stale ładowanie i zwalnianie rejestrów kod, który umożliwia procesora do przechowywania danych w rejestrze i wielokrotnie do niego dostęp. Aby ułatwić kompilator, aby przechowywać dane w rejestrach i wykonywać inne optymalizacje, należy unikać używania zmiennych globalnych i zależą od zmiennych lokalnych, jak to możliwe. Kod napisany w ten sposób jest nazywany mają dobrej miejscowości odwołania. W przypadku niektórych języków, takich jak C/C++ programistę można zadeklarować zmiennej rejestru, który informuje kompilator, aby spróbuj najlepiej jest, aby zachować zmiennej w rejestrze przez cały czas. Aby uzyskać więcej informacji, zobacz [zarejestrować — słowo kluczowe](http://msdn.microsoft.com/en-us/5b66905a-2f7f-4918-bb55-5e66d4bc50f9).  
  
 Rejestruje można podzielić na dwa typy: ogólnego przeznaczenia i specjalne. Rejestruje ogólnego przeznaczenia przechowywania danych dla ogólnych operacji, takich jak dodawanie dwóch liczb lub odwołuje się do elementu w tablicy. Rejestruje specjalny ma określonych celów oraz specjalne znaczenie. Dobrym przykładem jest rejestrze wskaźnik stosu, który procesor jest używane do śledzenia stosu wywołań programu. Dla programisty będzie prawdopodobnie nie manipulować wskaźnik stosu bezpośrednio. Jednak jest niezbędne do sprawnego funkcjonowania programu, ponieważ bez wskaźnik stosu procesora może nie wiedzieć, gdzie powrócić do końca wywołania funkcji.  
  
 Większość rejestrów ogólnego przeznaczenia przechowywane tylko danych jednego elementu. Na przykład pojedynczy liczba całkowita, liczba zmiennoprzecinkowa lub elementu tablicy. Niektóre nowsze mieć większe rejestrów, nazywany rejestrów wektora, zawierających mała tablica danych. Ponieważ posiadają bardzo dużo danych rejestrów wektor zezwala na operacje dotyczące tablice wykonywane bardzo szybko. Wektor rejestrów najpierw były używane na superkomputerów kosztownych, wysokiej wydajności, ale teraz stają się dostępne na mikroprocesorami, gdzie są używane do wykorzystanie w znacznym operacje graficzne.  
  
 Procesor ma zazwyczaj dwa zestawy rejestrów ogólnego przeznaczenia, jeden zoptymalizowane pod kątem operacji zmiennoprzecinkowych i innych operacjach liczby całkowitej. Spodziewać są one nazywane zmiennoprzecinkowych i rejestruje liczbę całkowitą.  
  
 Kod zarządzany jest kompilowana w czasie wykonywania do kodu macierzystego, który uzyskuje dostęp do rejestrów fizyczny procesor. **Rejestruje** okno wyświetla te fizycznych rejestruje środowisko uruchomieniowe języka wspólnego lub kodu natywnego. **Rejestruje** okna nie są wyświetlane informacje do rejestru dla skryptu lub aplikacji SQL, ponieważ skrypt i SQL są języki, które nie obsługują koncepcji rejestrów.  
  
 Aby uzyskać więcej informacji na temat wyświetlania **rejestruje** okna, zobacz [korzystanie z okna rejestrów](../debugger/how-to-use-the-registers-window.md).  
  
 Podczas przeglądania **rejestruje** okna, zobaczysz wpisów, np. w tym przykładzie:  
  
```  
EAX = 003110D8  
```  
  
 Symbol z lewej strony logowania = jest nazwa rejestru, EAX, w tym przypadku. Liczba z prawej strony logowania = reprezentuje zawartość rejestru.  
  
 **Rejestruje** okna umożliwia wykonanie więcej niż tylko widok zawartości rejestru. Podczas pracy w trybie przerwania w kodzie natywnym, można kliknij zawartość rejestru i edytować wartość. Nie jest to coś, co należy zrobić losowo. Bez zrozumienia rejestru, którą edytujesz, a dane, które zawiera, w wyniku edycji careless jest prawdopodobnie awarię programu lub niepożądane skutki. Niestety szczegółowy opis zestawów rejestru dla różnych procesorów Intel i zgodnych z Intel daleko wykracza poza zakres to krótkie wprowadzenie.  
  
## <a name="register-groups"></a>Grupy rejestru  
 Aby zwiększyć czytelność, **rejestruje** okna organizuje rejestrów w grupach. Kliknięcie prawym przyciskiem myszy na **rejestruje** , zostaną wyświetlone menu podręczne zawierające listę grup, które można wyświetlić lub ukryć zgodnie z własnymi potrzebami.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Korzystanie z okna rejestrów](../debugger/how-to-use-the-registers-window.md)   
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)