---
title: Tworzenie wystąpień projektu za pomocą fabryk projektów przez ustawienie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b3a59eee6701caf0b4d3b56df273b280f8bf6ece
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="creating-project-instances-by-using-project-factories"></a>Tworzenie wystąpień projektu za pomocą fabryk projektu
Typy w projektów [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] użyj *fabrykę projektów* do tworzenia wystąpień obiektów projektu. Fabryka projektu jest podobna do fabrykę klas standardowe cocreatable obiektów COM. Obiekty projektu nie są jednak cocreatable: ich można tworzyć tylko za pomocą fabryki projektu.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE wywołuje fabrykę projektów zaimplementowana w pakiecie VSPackage, gdy użytkownik załaduje istniejącego projektu lub tworzy nowy projekt w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Nowy obiekt projektu zawiera IDE wystarczającej ilości informacji do wypełnienia Eksploratora rozwiązań. Nowy obiekt projektu zapewnia również wymaganych interfejsów do obsługi wszystkich odpowiednich akcji interfejsu użytkownika inicjowane przez środowisko IDE.  
  
 Można zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> interfejsu w klasie w projekcie. Zazwyczaj znajduje się on w jego własnej modułu.  
  
 Na przykład implementacja `IVsProjectFactory` interfejsu, zobacz PrjFac.cpp, który jest zawarty w [podstawowego projektu](http://msdn.microsoft.com/en-us/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) katalog przykładu.  
  
 Projekty, które obsługują agregowana przez właściciela muszą zostać zachowane właściciela klucz w pliku projektu. Gdy <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> metoda jest wywoływana w projekcie przy użyciu klucza właściciela, należących do projektu konwertuje kluczem właściciela fabrykę projektów, następnie wywołuje GUID `CreateProject` metody w tej fabryce projektu do tworzenia rzeczywistych.  
  
## <a name="creating-an-owned-project"></a>Tworzenie projektu należące do firmy  
 Właściciel tworzy należących do projektu w dwóch fazach:  
  
1.  Wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> metody. Zapewnia możliwość tworzenia obiektu zagregowane projektu, w oparciu o wejściowych kontrolowanie należących do projektu `IUnknown`. Należących do projektu przekazuje wewnętrzny `IUnknown` i zagregowane obiektu do właściciela projektu. Daje możliwość przechowywania wewnętrzny należących do projektu `IUnknown`.  
  
2.  Wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> metody. Należących do projektu nie wszystkie jego wystąpienia, gdy ta metoda jest wywoływana zamiast wywoływać metodę `IVsProjectFactory::CreateProject` jako może być w przypadku projektów, które nie należą do firmy. Dane wejściowe `VSOWNEDPROJECTOBJECT` wyliczenie jest zwykle zagregowane należących do projektu. Należących do projektu można użyć tej zmiennej do określenia, czy jego obiekt projektu został już utworzony (plik cookie nie jest równa NULL) lub musi zostać utworzony (plik cookie jest równa NULL).  
  
 Typy projektów są identyfikowane przez unikatowy identyfikator GUID podobny do identyfikatora CLSID obiektu COM cocreatable projektu. Zazwyczaj jeden projekt fabryki dojść do tworzenia wystąpienia typu pojedynczego projektu, chociaż można mieć jeden fabrykę projektów obsłużyć więcej niż jeden identyfikator GUID typu projektu.  
  
 Typy projektów są skojarzone z określonym rozszerzeniem nazwy. Gdy użytkownik próbuje otworzyć istniejący plik projektu lub podejmuje próbę utworzenia nowego projektu w klonowania szablonu, IDE używa rozszerzenia pliku w celu określenia odpowiedniego identyfikatora GUID projektu.  
  
 Jak IDE Określa, czy należy utworzyć nowy projekt lub otworzyć istniejącego projektu określonego typu, IDE używa tych informacji do rejestru systemu, w obszarze [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects] do ustalone, które Pakiet VSPackage implementuje fabrykę projektów wymagane. IDE ładuje tym pakiecie VSPackage. W <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metody, pakiet VSPackage należy zarejestrować jego fabrykę projektów z IDE przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> metody.  
  
 Podstawową metodą `IVsProjectFactory` interfejs jest <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> który powinna obsługiwać dwa scenariusze: otwierania istniejącego projektu i tworzenia nowego projektu. Większości projektów przechowywanie ich stanu projektu w pliku projektu. Zazwyczaj nowe projekty są tworzone przez tworzenie kopii pliku szablonu przekazany do `CreateProject` — metoda, a następnie otworzyć. Istniejące projekty zostały utworzone przez bezpośrednie otwieranie pliku projektu przekazany do `CreateProject` metody. `CreateProject` Metody można wyświetlić dodatkowe funkcje interfejsu użytkownika dla użytkownika, w razie potrzeby.  
  
 Projekt można również używać żadnych plików i należy przechowywać stanu projekt w mechanizmie magazynu innego niż system plików, takich jak bazy danych lub serwera sieci Web. W takim przypadku przekazany parametr nazwy pliku do `CreateProject` — metoda nie jest rzeczywiście ścieżki systemu plików, ale unikatowy ciąg — adres URL — Aby zidentyfikować dane projektu. Nie należy skopiować pliki szablonów, które są przekazywane do `CreateProject` do wyzwolenia sekwencji konstrukcji odpowiednie do wykonania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [Lista kontrolna: tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)