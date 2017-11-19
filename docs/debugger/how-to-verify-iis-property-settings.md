---
title: "Porady: Weryfikacja właściwości ustawień IIS | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- IIS, property settings
- debugging Web applications, troubleshooting
- IIS administration tool
- Web applications, setting properties
- properties [debugger], setting with IIS administration tool
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c0d58ea851423e9239d8685f89890b5d9e152d53
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-verify-iis-property-settings"></a>Porady: weryfikacja właściwości ustawień IIS
Można ustawić właściwości dla aplikacji sieci Web za pomocą narzędzia administracyjnego IIS. Te właściwości muszą być ustawione poprawnie dla aplikacji do uruchomienia, więc weryfikacji tych ustawień jest często krokiem w rozwiązywaniu problemów.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-check-iis-settings-for-the-web-application"></a>Aby sprawdzić ustawienia usług IIS dla aplikacji sieci Web  
  
1.  Otwórz **narzędzia administracyjne** okna: na **Start** menu wskaż **programy**, a następnie kliknij przycisk **narzędzia administracyjne**. Jeśli **narzędzia administracyjne** nie ma **programy** menu, a następnie wyszukaj go w **Panelu sterowania**.  
  
    -   W systemie Windows 2000, wybierz **Menedżera internetowych usług**.  
  
    -   W systemie Windows XP, wybierz **Internetowe usługi informacyjne**.  
  
    -   W systemie Windows Server 2003, kliknij dwukrotnie **Zarządzanie serwerem**.  
  
         **Zarządzanie serwerem** zostanie otwarte okno. W obszarze **serwera aplikacji**, kliknij przycisk **zarządzania tym serwerem aplikacji**.  
  
         **Serwera aplikacji** zostanie otwarte okno. Otwórz **Internet Information Services (IIS) Manager** węzła w okienku po lewej stronie.  
  
2.  W oknie dialogowym kliknij węzeł drzewa sterowania komputera. Kliknij przycisk **witryn sieci Web** węzeł i wybierz węzeł aplikacji sieci Web. Albo będzie węzeł witryny sieci Web, a w związku z tym elementem równorzędnym **domyślna witryna sieci Web** węzła lub węzła katalogu wirtualnego poniżej istniejący węzeł witryny sieci Web.  
  
3.  Kliknij prawym przyciskiem myszy aplikację sieci Web, a następnie w menu skrótów kliknij **właściwości**.  
  
4.  Sprawdź ustawienia zabezpieczeń dla aplikacji sieci Web:  
  
    1.  W aplikacji sieci Web **właściwości** okna, kliknij przycisk **zabezpieczenia katalogu** , a następnie kliknij pozycję **Edytuj**.  
  
    2.  W **metod uwierzytelniania** okno dialogowe, wybierz opcję **Włącz dostęp anonimowy** i **zintegrowanego uwierzytelniania systemu Windows** Jeśli nie są już wybrane.  
  
    3.  Kliknij przycisk **OK** zamknąć **metod uwierzytelniania** okno dialogowe.  
  
5.  Dla aplikacji serwera ATL. Sprawdź, czy zlecenie DEBUG jest skojarzona z rozszerzeniem ISAPI. Aby uzyskać więcej informacji, zobacz [porady: kojarzenie zlecenie debugowania z rozszerzeniem](http://msdn.microsoft.com/en-us/50d261d3-4bd4-41c0-b44e-3591086f121e).  
  
6.  Dla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji, sprawdź, czy folder wirtualny dla aplikacji ma nazwę aplikacji w **Internet Information Services (IIS) Manager**, **Menedżera internetowych usług** lub  **Internetowe usługi informacyjne**.  
  
    1.  W aplikacji sieci Web **właściwości** wybierz **katalogu** karcie, jeśli aplikacja znajduje się w katalogu wirtualnego, lub **katalog macierzysty** karcie, jeśli aplikacja jest w Witryna sieci Web.  
  
    2.  Sprawdź, czy nazwa w **ścieżka lokalna** jest zgodna z nazwą katalogu, w którym aplikacja została faktycznie wdrożona.  
  
    3.  W obszarze **ustawienia aplikacji**, wpisz nazwę katalogu głównego, który zawiera aplikację.  
  
    4.  Kliknij przycisk **OK** zamknąć **właściwości** okno dialogowe.  
  
7.  Dla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji, kliknij przycisk **ASP.NET** kartę i sprawdź, czy prawidłowa wersja [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] jest określona.  
  
8.  Kliknij przycisk **OK** zamknąć **właściwości** okno dialogowe.  
  
9. Kliknij przycisk **OK** zamknąć **Internet Information Services (IIS) Manager**, **Menedżera usług internetowych**, lub **Internetowe usługi informacyjne**okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązywanie problemów](../debugger/debugging-web-applications-troubleshooting.md)