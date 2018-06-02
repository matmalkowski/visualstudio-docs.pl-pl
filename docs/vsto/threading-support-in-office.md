---
title: Obsługa wątkowości w pakietu Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- multiple threads [Office development in Visual Studio]
- threading [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], threading support
- object models [Office development in Visual Studio], threading support
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 966f012b2ff4860205186410951b759c2e214668
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693087"
---
# <a name="threading-support-in-office"></a>Obsługa wątkowości w pakietu Office
  Ten artykuł zawiera informacje dotyczące sposobu wątków jest obsługiwana w modelu obiektów programu Microsoft Office. Model obiektów pakietu Office nie jest bezpieczne dla wątków, ale istnieje możliwość pracy z wielu wątków w rozwiązaniach pakietu Office. Aplikacje pakietu Office są serwery składnika modelu COM (Object). COM pozwala klientom wywoływać serwerów COM na dowolne wątków. W przypadku serwerów COM, które nie są bezpieczne dla wątków COM udostępnia mechanizm do serializacji równoczesnych wywołań, tak aby tylko jeden wątek logiczny jest wykonywana na serwerze w dowolnym momencie. Mechanizm ten nosi nazwę modelu jednowątkowego apartamentu (STA). Ponieważ wywołania są serializowane, wywołań może zostać zablokowany przez czas, gdy serwer jest zajęty lub obsługuje inne wywołania wątku w tle.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="knowledge-required-when-using-multiple-threads"></a>Wymagana wiedza, korzystając z wielu wątków  
 Aby pracować z wielu wątków, musi mieć co najmniej podstawową wiedzę na temat następujących aspektów wielowątkowość:  
  
-   Interfejsy API systemu Windows  
  
-   COM pojęcia wielowątkowe  
  
-   Współbieżność  
  
-   Synchronizacja  
  
-   Organizowanie  
  
 Aby uzyskać ogólne informacje o wielowątkowości, zobacz [zarządzana wątkowość](/dotnet/standard/threading/).  
  
 Office działa w głównym pozostaje tryb komórek jednowątkowych Opis skutków to umożliwia zrozumienie, jak używać wielu wątków w pakiecie Office.  
  
## <a name="basic-multithreading-scenario"></a>Podstawowy scenariusz wielowątkowości  
 Kod w rozwiązaniach pakietu Office jest zawsze uruchamiany w głównym wątku interfejsu użytkownika. Możesz chcieć wygładzanie wydajność aplikacji przez uruchomienie oddzielnych zadań na wątku w tle. Celem jest wykonać dwie czynności pozornie jednocześnie zamiast jednego zadania zostały wykonane przez inne, co powinno spowodować wykonanie płynniejszy (główną przyczyną Użyj wielu wątków). Na przykład może być kodu zdarzeń w głównym wątku interfejsu użytkownika programu Excel i wątku w tle może uruchomić zadania, która zbiera dane z serwera i aktualizuje komórek w Interfejsie użytkownika programu Excel przy użyciu danych z serwera.  
  
## <a name="background-threads-that-call-into-the-office-object-model"></a>Wątki w tle, które wywołują modelu obiektów pakietu Office  
 Gdy wątku w tle wywołuje aplikacji pakietu Office, wywołanie jest automatycznie zorganizować granicy STA. Jednak nie ma żadnej gwarancji, że aplikacji pakietu Office może obsłużyć wywołania w tym czasie wątku w tle powoduje, że jej. Istnieje kilka możliwości:  
  
1.  W aplikacji pakietu Office musi pompa wiadomości dla wywołania mieć możliwość wprowadzania. Jeśli wykonywanie operacji może potrwać ciężki przetwarzania bez otrzymania to.  
  
2.  Jeśli inny wątek logicznej jest już w apartamencie, nie można wprowadzić nowego wątku. Dzieje się tak często, gdy logicznego wątku wprowadza aplikacji pakietu Office, a następnie wprowadza współużytkowane wywołanie apartamentu obiektu wywołującego. Aplikacja została zablokowana oczekiwania dla tego wywołania do zwrócenia.  
  
3.  Program Excel może być w stanie tak, aby natychmiast nie może on obsługiwać połączenia przychodzącego. Na przykład aplikacji pakietu Office może wyświetlenie modalnego okna dialogowego.  
  
 Możliwości 2 i 3, zapewnia COM [IMessageFilter](http://msdn.microsoft.com/en-us/e12d48c0-5033-47a8-bdcd-e94c49857248) interfejsu. Jeśli serwer ją implementuje, wszystkie wywołania wprowadź za pośrednictwem [HandleIncomingCall](http://msdn.microsoft.com/en-us/7e31b518-ef4f-4bdd-b5c7-e1b16383a5be) metody. Możliwości 2 wywołania są automatycznie odrzucane. Możliwość 3 serwer można odrzucić wywołanie, w zależności od okoliczności. Jeśli połączenie zostanie odrzucony, wywołujący musi podejmowania decyzji. Zwykle implementuje wywołującego [IMessageFilter](http://msdn.microsoft.com/en-us/e12d48c0-5033-47a8-bdcd-e94c49857248), w którym to przypadku będą otrzymywać powiadomienia o odrzucenie przez [RetryRejectedCall](http://msdn.microsoft.com/en-us/3f800819-2a21-4e46-ad15-f9594fac1a3d) — metoda.  
  
 Jednak w przypadku rozwiązania utworzone przy użyciu narzędzi programowania pakietu Office w Visual Studio, współdziałanie z COM konwertuje wszystkie odrzucone wywołań <xref:System.Runtime.InteropServices.COMException> ("filtr wiadomości wykazał, że aplikacja jest zajęta"). Po każdej zmianie wprowadzeniu model obiektowy wywołania wątku w tle, muszą być przygotowane do obsługi tego wyjątku. Zwykle obejmujące ponowną próbą przez pewien czas i wyświetlania okna dialogowego. Można jednak również utworzyć wątku w tle jako STA i zarejestruj filtr komunikatu dla tego wątku do obsługi tej sprawy.  
  
## <a name="start-the-thread-correctly"></a>Poprawne uruchomienie wątku  
 Podczas tworzenia nowego wątku STA, Ustaw stan apartamentu STA przed rozpoczęciem wątku. W poniższym przykładzie pokazano, jak to zrobić.  
  
 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]  
  
 Aby uzyskać więcej informacji, zobacz [zarządzana wątkowość — najlepsze praktyki](/dotnet/standard/threading/managed-threading-best-practices).  
  
## <a name="modeless-forms"></a>Niemodalne formularzy  
 Niemodalny formularz umożliwia pewien typ interakcji z aplikacją, gdy formularz jest wyświetlany. Użytkownik wchodzi w interakcję z formularza i formularz współdziała z aplikacji bez zamknięcia. Model obiektów pakietu Office obsługuje zarządzanych formularze niemodalne; jednak ich nie powinien być używany na wątku w tle.  
  
## <a name="see-also"></a>Zobacz także  
 [Zarządzana wątkowość](/dotnet/standard/threading/)  
 [Wątkowość (C#)](/dotnet/csharp/programming-guide/concepts/threading/index) [wątkowość (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)   
 [Użyj wątki i wątkowość](/dotnet/standard/threading/using-threads-and-threading)   
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)  
  
  