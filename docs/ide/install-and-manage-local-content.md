---
title: "Zainstaluj lokalną dokumentację programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-help-viewer
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: hv_manage
helpviewer_keywords:
- changing content installation source [Help Viewer]
- updating local content [Help Viewer]
- Help Viewer, content installation source
- Help Viewer, updating local content
- Help Viewer, changing content installation source
- installing local content [Help Viewer]
- content installation source [Help Viewer]
- downloading content [Help Viewer]
- removing local content [Help Viewer]
- Help Viewer, removing local content
- Help Viewer, installing local content
- Help Viewer, downloading content
ms.assetid: efd9df4c-2e69-4c50-992c-9678a8d8cf19
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3bd498004568bab80565782e11b46691a7d0ef1f
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2017
---
# <a name="install-and-manage-local-content"></a>Zainstaluj i Zarządzaj zawartości lokalnej
Za pomocą Podglądu pomocy firmy Microsoft, można dodać, usunąć, aktualizacji i przenieść zawartości pomocy, która jest zainstalowana na komputerze, aby spełniały Twoje potrzeby rozwoju oprogramowania.  
  
Aby zarządzać zawartości na komputerze lokalnym, musisz zalogować się przy użyciu konta z uprawnieniami administratora. Ponadto nie można zarządzać lokalnej zawartości podczas pracy w środowisku przedsiębiorstwa, ponieważ administratorzy systemu może podejmowanie tych decyzji dotyczących organizacji. Aby uzyskać więcej informacji, zobacz [Podręcznik administratora programu Podgląd Pomocy](../ide/help-viewer-administrator-guide.md).  
  
## <a name="changing-the-content-installation-source"></a>Zmiana źródła instalacji zawartości  
Domyślnie Podgląd pomocy instalację zawartości przy użyciu usługi online firmy Microsoft jako źródło. Zazwyczaj nie zmienisz źródła zawartości chyba, że pracujesz w środowisku firmowym, dla której administrator systemu zainstalował już zawartości w innej lokalizacji.  
  
#### <a name="to-change-the-content-installation-source"></a>Aby zmienić źródło instalacji zawartości  
  
1.  Na **zarządzania zawartością** , wybierz pozycję **dysku** przycisk opcji.  
  
    > [!NOTE]
    >  **Dysku** opcja jest niedostępna, jeśli administrator uniemożliwił modyfikowanie źródła instalacji zawartości. Aby uzyskać więcej informacji, zobacz [Podręcznik administratora programu Podgląd Pomocy](../ide/help-viewer-administrator-guide.md).  
  
2.  Wykonaj jedną z następujących czynności:  
  
    -   Wprowadź ścieżkę do pliku .msha lub adres URL punktu końcowego usługi.  
  
    -   Kliknij przycisk Przeglądaj (**...** ) przycisk, aby przejść do pliku .msha.  
  
    -   Na liście wybierz polecenie wpisu, który został ostatnio używanych.  
  
## <a name="download-and-install-content-locally"></a>Pobierz i zainstaluj zawartość lokalnie  
Jeśli pobrać i zainstalować zawartość na komputerze lokalnym, można wyświetlić tematy, gdy nie ma połączenia internetowego.  
  
> [!IMPORTANT]
> Aby zainstalować zawartość, należy zalogować się przy użyciu konta z uprawnieniami administracyjnymi.  
  
> [!NOTE]
> Jeśli ustawiono programu Visual Studio IDE języka innego niż angielski, można zainstalować zawartości w języku angielskim i zlokalizowanej zawartości. Jednak żadnej zawartości pojawi się zainstalowanie wersji angielskiej i **obejmują angielskim zawartości we wszystkich kartach nawigacji i żądaniach F1** pole wyboru w **Opcje aplikacji Viewer** okno dialogowe jest wyczyszczone.  
  
#### <a name="to-download-and-install-content"></a>Aby pobrać i zainstalować zawartość  
  
1.  Wybierz **zarządzania zawartością** kartę.  
  
2.  Na liście zawartości, wybierz **Dodaj** link obok książki lub książek, które chcesz pobrać i zainstalować.  
  
     Książce jest dodawany do **oczekujące zmiany** listy i szacowany rozmiar książki lub książek określonych pojawia się poniżej tej listy. Ponieważ niektóre książek udostępnić tematy, rozmiar całkowitą pobierania wielu książek może być mniejszy niż wynik zsumowanie rozmiary książki, co określony.  
  
3.  Wybierz **aktualizacji** przycisku.  
  
     Książki lub książek, które są instalowane wraz wszelkie aktualizacje książki, które mają już na komputerze. Termin instalacji różny, ale można wyświetlić postęp na pasku stanu.  
  
## <a name="removing-local-content"></a>Usuwanie zawartości lokalnej  
Przez usunięcie niechcianych zawartości z komputera, można zaoszczędzić miejsce na dysku.  
  
> [!IMPORTANT]
> Musi mieć uprawnienia administracyjne, aby usunąć zawartość.  
  
> [!NOTE]
> Nie zawartość jest wyświetlana, jeśli środowiska IDE programu Visual Studio jest ustawiony na języku innym niż angielski, należy usunąć zlokalizowanej zawartości i **obejmują angielskim zawartości we wszystkich karty nawigacji i żądaniach F1** pole wyboru w **Opcje aplikacji Viewer** okno dialogowe jest wyczyszczone.  
  
#### <a name="to-remove-content"></a>Aby usunąć zawartość  
  
1.  Wybierz **zarządzania zawartością** kartę.  
  
2.  Na liście zawartości, wybierz **Usuń** link obok książki lub książek, które mają zostać usunięte.  
  
     Książce jest dodawany do **oczekujące zmiany** listy.  
  
3.  Wybierz **aktualizacji** przycisku.  
  
     Książki lub książek określone przez użytkownika są usuwane z komputera.  
  
## <a name="updating-local-content"></a>Aktualizowanie zawartości lokalnej  
 Pasek stanu wskazuje, kiedy są dostępne aktualizacje do zainstalowanych zawartości.  
  
> [!IMPORTANT]
>  Jeśli chcesz, aby Podgląd pomocy, aby automatycznie sprawdzać dostępność aktualizacji w trybie online, należy otworzyć **Opcje aplikacji Viewer** okno dialogowe, a następnie wybierz **przejść do trybu online, aby sprawdzić aktualizacje zawartości** pole wyboru.  
  
#### <a name="to-update-local-content"></a>Aby zaktualizować zawartość lokalnego  
  
-   W prawym dolnym rogu paska stanu, wybierz **kliknij tutaj, aby pobrać teraz** łącza.  
  
 Czas aktualizacji może się różnić, ale na pasku stanu jest wyświetlany postęp aktualizacji.  
  
## <a name="moving-local-content"></a>Przenoszenie zawartości lokalnej  
 Przenosząc zainstalowaną zawartość z komputera lokalnego do udziału sieciowego lub innej partycji na komputerze lokalnym, można zaoszczędzić miejsce na dysku.  
  
> [!IMPORTANT]
>  Aby przenieść zawartość, musisz zalogować się przy użyciu konta z uprawnieniami administracyjnymi.  
  
#### <a name="to-move-local-content"></a>Aby przenieść zawartości lokalnej  
  
1.  Na **zarządzania zawartością** , wybierz pozycję **Przenieś** przycisku w obszarze **lokalnej ścieżki magazynu**.  
  
     **Przenoszenia zawartości** zostanie otwarte okno dialogowe.  
  
2.  W **do** polu tekstowym Wprowadź inną lokalizację zawartości, a następnie wybierz **OK** przycisku.  
  
3.  Wybierz **Zamknij** przycisk po przeniesieniu zawartości.  
  
## <a name="see-also"></a>Zobacz także  
[Podgląd Pomocy firmy Microsoft](../ide/microsoft-help-viewer.md)