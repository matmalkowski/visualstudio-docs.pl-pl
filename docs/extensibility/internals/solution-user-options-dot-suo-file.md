---
title: "Opcje użytkownika rozwiązania (. Pliku suo) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0bca2eef930b871d5728ff1c85742a28f4b51a7e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="solution-user-options-suo-file"></a>Opcje użytkownika rozwiązania (. Pliku suo)
Plik rozwiązania użytkownika opcje (.suo) zawiera opcje rozwiązania dla poszczególnych użytkowników. Nie można zaewidencjonować ten plik do kontroli kodu źródłowego.  
  
 W pliku opcji (.suo) rozwiązania jest magazynem strukturalnym lub złożone, przechowywane w formacie binarnym pliku. Informacje o użytkowniku do strumieni zapisywania o tej nazwie jest klucz, który będzie służyć do identyfikowania informacji w pliku .suo strumienia. Plik opcji użytkownika rozwiązania jest używany do przechowywania ustawień preferencji użytkownika i jest tworzona automatycznie podczas Visual Studio zapisuje rozwiązania.  
  
 Jeśli środowisko otwarty plik .suo, wylicza wszystkie aktualnie załadowanych VSPackages. Jeśli pakiet VSPackage implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interfejs, a następnie wywołania środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> metoda VSPackage prosząc go załadować wszystkie jej dane z pliku .suo.  
  
 Jest to pakiet VSPackage odpowiedzialność wiedzieć, jaki prześle strumieniowo może być zapisany w pliku .suo. Dla każdego strumienia, który zapisał pakiet VSPackage wywołuje do środowiska za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> można załadować określonego strumienia, który jest identyfikowany przez klucz, który jest nazwą strumienia. Środowisko wywołuje wstecz do pakiet VSPackage można odczytać określonego strumieniu Nazwa strumienia i `IStream` wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> metody.  
  
 W tym momencie innego wywołania mającego na celu `LoadUserOptions` czy jest innej sekcji plik .suo, który ma być do odczytu. Ten proces jest kontynuowany, dopóki wszystkie strumienie danych w pliku .suo odczytane i przetwarzane przez środowisko.  
  
 Po zapisaniu lub zamknięty wywołania środowiska rozwiązania <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> metody za pomocą wskaźnika do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> metody. `IStream` Zawierający dane binarne do zapisania jest przekazywana do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> metodę, która następnie zapisuje informacje w pliku .suo wywołania `SaveUserOptions` metody ponownie, aby sprawdzić, czy inny strumień informacji do zapisu .suo plik.  
  
 Te dwie metody `SaveUserOptions` i `WriteUserOptions`, są nazywane rekursywnie dla każdego strumienia danych można zapisać do pliku .suo, przekazując wskaźnik do `IVsSolutionPersistence`. Są one nazywane cyklicznie, aby umożliwić zapis wielu strumieni w pliku .suo. W ten sposób informacje o użytkowniku jest trwały z rozwiązaniem i może być przy następnym otwarciu rozwiązania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [Rozwiązania](../../extensibility/internals/solutions.md)