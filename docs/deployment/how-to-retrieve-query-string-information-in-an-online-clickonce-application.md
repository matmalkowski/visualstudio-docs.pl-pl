---
title: 'Porady: pobieranie informacji o ciągu kwerendy w aplikacji ClickOnce w trybie Online | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, query strings
- query strings, retrieving information
ms.assetid: 48ce098a-a075-481b-a5f5-c8ba11f63120
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: ae316f8ed84658c96d78f25f2aaf9c64a800d42c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-retrieve-query-string-information-in-an-online-clickonce-application"></a>Porady: pobieranie informacji o ciągu zapytania w aplikacji ClickOnce w trybie online
*Ciągu zapytania* jest to część adresem URL zaczynającym się znakiem zapytania (?) zawierający dowolne informacje w formularzu *nazwa = wartość*. Załóżmy, że masz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikację o nazwie `WindowsApp1` hostującego na `servername`, i chcesz przekazać wartość zmiennej `username` po uruchomieniu aplikacji. Adres URL może wyglądać następująco:  
  
 `http://servername/WindowsApp1.application?username=joeuser`  
  
 Poniższe dwie procedury pokazują, jak używać [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji w celu uzyskania informacji o ciągu zapytania.  
  
> [!NOTE]
>  Można tylko przekazać informacje w ciągu zapytania, gdy aplikacja jest jest uruchamiana przy użyciu protokołu HTTP, zamiast używać udziału plików lub lokalnego systemu plików.  
  
 W pierwszej procedury przedstawiono sposób z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja może używać małych fragment kodu do odczytu tych wartości, po uruchomieniu aplikacji.  
  
 Następna procedura przedstawia sposób konfigurowania programu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji za pomocą MageUI.exe, dzięki czemu może akceptować parametrów ciągu zapytania. Należy to zrobić, gdy opublikujesz aplikację.  
  
> [!NOTE]
>  Przed podjęciem decyzji o włączenie tej funkcji, zobacz sekcję "Zabezpieczenia" w dalszej części tego tematu.  
  
 Aby uzyskać informacje o sposobie tworzenia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia przy użyciu Mage.exe lub MageUI.exe, zobacz [wskazówki: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
> [!NOTE]
>  Począwszy od programu .NET Framework 3.5 z dodatkiem SP1, jest to możliwe przekazać argumenty wiersza polecenia do trybu offline [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. Jeśli chcesz podać argumenty do aplikacji, można przekazać w parametrach do pliku skrótu. Rozszerzenie APPREF MS.  
  
### <a name="to-obtain-query-string-information-from-a-clickonce-application"></a>Uzyskanie informacji o ciągu zapytania od aplikacji ClickOnce  
  
1.  Umieść następujący kod w projekcie. Aby ten kod, aby funkcja, konieczne będzie mieć odwołanie do System.Web i Dodaj `using` lub `Imports` instrukcje System.Web, System.Collections.Specialized i System.Deployment.Application.  
  
     [!code-csharp[ClickOnceQueryString#1](../deployment/codesnippet/CSharp/how-to-retrieve-query-string-information-in-an-online-clickonce-application_1.cs)]
     [!code-vb[ClickOnceQueryString#1](../deployment/codesnippet/VisualBasic/how-to-retrieve-query-string-information-in-an-online-clickonce-application_1.vb)]  
  
2.  Wywołanie funkcji wcześniej zdefiniowane pobrać <xref:System.Collections.DictionaryBase.Dictionary%2A> z parametrów ciągu zapytania indeksowane według nazwy.  
  
### <a name="to-enable-query-string-passing-in-a-clickonce-application-with-mageuiexe"></a>Aby umożliwić przekazywanie w aplikacji ClickOnce z MageUI.exe ciąg zapytania  
  
1.  Otwórz wiersz polecenia .NET, wpisz:  
  
    ```  
    MageUI  
    ```  
  
2.  Z **pliku** menu, wybierz opcję **Otwórz**i Otwórz plik manifestu wdrożenia dla użytkownika [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, które są pliku kończy się rozszerzeniem `.application` rozszerzenia.  
  
3.  Wybierz **opcje wdrażania** panelu w oknie nawigacji po lewej stronie, a następnie wybierz **Zezwalaj na adres URL parametry do przekazania do aplikacji** pole wyboru.  
  
4.  Z **pliku** menu, wybierz opcję **zapisać**.  
  
> [!NOTE]
>  Alternatywnie można włączyć ciąg zapytania, przekazując [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Wybierz **Zezwalaj na adres URL parametry do przekazania do aplikacji** pola wyboru, które można znaleźć, otwierając **właściwości projektu**, wybierając żądane **publikowania** kartę, klikając pozycję **Opcje** przycisk, a następnie wybierając **manifesty**.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Korzystając z parametrów ciągu zapytania, użytkownik musi dokładnie rozważyć sposób aplikacji jest zainstalowany i aktywowany. Jeśli aplikacja jest skonfigurowana do zainstalowania na komputerze użytkownika z sieci Web lub w udziale sieciowym, jest prawdopodobne, że użytkownik będzie aktywowania aplikacji tylko raz przy użyciu adresu URL. Po utworzeniu tego użytkownika zwykle uaktywni aplikację za pomocą skrótu w **Start** menu. W związku z tym aplikacji jest gwarantowana do odbierania przez jego okres istnienia argumenty ciągu zapytania tylko raz. Jeśli chcesz przechowywać tych argumentów na komputerze użytkownika do użytku w przyszłości jest odpowiedzialny za przechowywania ich w sposób bezpieczny i bezpieczne.  
  
 Jeśli aplikacja jest w trybie online tylko, zawsze będą aktywowane przy użyciu adresu URL. Nawet w tym przypadku jednak aplikacji musi być przystosowana do działają poprawnie, jeśli parametry ciągu zapytania lub są uszkodzone.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Zezwalaj na przekazywanie parametrów adresu URL do Twojej [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji tylko wtedy, gdy planujesz czyszczenia danych wejściowych znaków złośliwego przed jego użyciem. Ciąg osadzony oferty, ukośniki lub średnikami, na przykład, może wykonywać dowolne dane operacje użycie niefiltrowane w zapytaniu SQL w bazie danych. Aby uzyskać więcej informacji o zabezpieczeniach ciąg zapytania, zobacz [Przegląd wykorzystuje skryptu](http://msdn.microsoft.com/Library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07).  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)