---
title: Zaawansowane ustawienia dla usług — okno dialogowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- vb.ProjectPropertiesAdvancedServices
helpviewer_keywords:
- Advanced Settings for Services dialog box
ms.assetid: 6dde4a2d-85e1-4275-aa55-24b84111be91
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51d3b8b8353bae0b4c0d308150a8834a27848d51
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="advanced-settings-for-services-dialog-box"></a>Zaawansowane ustawienia dla usług — Okno dialogowe
Usługi aplikacji klienta udostępnienia uproszczony [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] logowania, ról i usług profilu w aplikacjach formularzy systemu Windows i Windows Presentation Foundation (WPF). Można użyć **usług** strony **projektanta projektu** do konfigurowania usługi aplikacji klienta. Aby uzyskać więcej informacji na temat **usług** strony, zobacz [Strona usług, Projektant projektu](../../ide/reference/services-page-project-designer.md).  
  
 Użyj **Zaawansowane ustawienia dla usług** okna dialogowego **usług** strony **projektanta projektu** Aby skonfigurować ustawienia zaawansowane dla usług aplikacji klienta. Przy użyciu tych ustawień, można zastąpić niektóre domyślne zachowania usługi aplikacji na potrzeby mniej typowych scenariuszy. Aby uzyskać więcej informacji, zobacz [usługi aplikacji klienta](/dotnet/framework/common-client-technologies/client-application-services).  
  
 Aby uzyskać dostęp do **Zaawansowane ustawienia dla usług** okna dialogowego wybierz węzeł projektu w **Eksploratora rozwiązań**, a następnie kliknij przycisk **właściwości** na **projektu**  menu. Gdy **projektanta projektu** pojawia się, kliknij przycisk **usług** , a następnie kliknij pozycję **zaawansowane** przycisku. Kliknięcie tego przycisku zostanie wyłączone do czasu włączenia usługi aplikacji klienta.  
  
## <a name="task-list"></a>Lista zadań

- [Instrukcje: konfigurowanie usług aplikacji klienckich](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)

## <a name="uielement-list"></a>Lista elementów UI

 **Zapisz skrót hasła lokalnie, aby włączyć logowanie offline**  
 Określa, czy zaszyfrowane hasło użytkownika będą buforowane lokalnie umożliwia użytkownikowi na logowanie, gdy aplikacja jest w trybie offline. Ta opcja jest domyślnie wybrana.
  
 **Wymagać od użytkowników zalogować się ponownie przy każdym wygasa plik cookie z serwera**  
 Określa, czy wcześniej uwierzytelnieni użytkownicy są automatycznie ponownie uwierzytelnić gdy aplikacja uzyskuje dostęp do ról lub usługi profilu i plik cookie uwierzytelniania serwera utracił ważność. Wybierz tę opcję, aby odmówić dostępu do usług aplikacji i wymaga jawnego ponownego uwierzytelnienia, po wygaśnięciu pliku cookie. Jest to użyteczne w przypadku aplikacji wdrożonych w miejscach publicznych upewnij się, że zawsze uwierzytelniani użytkownicy uzyskują pozostaw aplikacji uruchomiony po nie pozostanie użycia. Ta opcja jest domyślnie wyczyszczone.  
  
 **Limit czasu pamięci podręcznej usługi roli**  
 Określa ilość czasu dostawcy roli klienta będzie używać wartości roli pamięci podręcznej zamiast uzyskiwanie dostępu do usługi ról. Mała wartość należy ustawić dany interwał czasu, gdy role są aktualizowane często lub większej wartości role są aktualizacji rzadko. Wartość domyślna to jeden dzień.  
  
 Dostawca roli uzyskuje dostęp do wartości pamięci podręcznej roli lub usługi ról podczas wywoływania <xref:System.Web.Security.RolePrincipal.IsInRole%2A> metody. Aby programowo wyczyścić pamięć podręczną i wymusić tę metodę w celu uzyskania dostępu do zdalnej usługi, należy wywołać <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A> metody.  
  
 **Użyj niestandardowych parametrów połączenia**  
 Określa, czy dostawcy usług klienta będą używać niestandardowego magazynu danych dla lokalnej pamięci podręcznej. Domyślnie dostawców usług będzie używać lokalnego systemu plików pamięci podręcznej. Wybranie tej opcji zostanie automatycznie wypełnić pole tekstowe z domyślnego ciągu połączenia. Możesz zachować domyślnego ciągu połączenia do automatycznego generowania i korzystania z bazy danych programu SQL Server Compact Edition, lub można określić parametry połączenia z istniejącą bazą danych programu SQL Server. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie usługi aplikacji klienta](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services). Ta opcja jest domyślnie wyczyszczone.  
  
## <a name="see-also"></a>Zobacz także

[Usługi aplikacji klienckich](/dotnet/framework/common-client-technologies/client-application-services)  
[Strona usług, Projektant projektu](../../ide/reference/services-page-project-designer.md)  
[Instrukcje: konfigurowanie usług aplikacji klienckich](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)