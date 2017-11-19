---
title: Strona podpisywania, Projektant projektu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.AddNewStrongNameKey
- ResolveKeySource.KeyFileForSignAssemblyNotImported
- vb.ProjectPropertiesSigning.ChangePasswordDialog
- ResolveKeySource.KeyFileForManifestNotImported
- vb.ProjectPropertiesSigning
- vb.ProjectPropertiesSigning.PasswordNeededDialog
- vb.ProjectPropertiesSigning.PfxPasswordDialog
helpviewer_keywords:
- Project Designer, Signing page
- Signing page in Project Designer
ms.assetid: dab3ba13-2f92-4827-92bd-1be3c35bc48b
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d193b8927019354244d6d80032ed0c761f584f83
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="signing-page-project-designer"></a>Strona podpisywania, Projektant projektu
Użyj **podpisywanie** strony **projektanta projektu** do podpisywania manifestów aplikacji i wdrażania, a także można podpisać zestawu (podpisywanie silną nazwą).  
  
 Zauważ, że podpisywania manifestów aplikacji i wdrażania jest procesem różne od podpisywania zestawu, mimo że oba zadania są wykonywane na **podpisywanie** strony.  
  
 Przechowywanie informacji plik klucza różni się również, manifestu podpisywania i podpisywanie zestawu. Do podpisywania manifestu klucza informacje są przechowywane w bazie danych magazynu kryptograficznego komputera i magazynu certyfikatów bieżącego użytkownika systemu Windows. Dla podpisywanie zestawu kluczy informacje są przechowywane tylko w bazie danych magazynu kryptograficznego tego komputera.  
  
 Aby uzyskać dostęp do **podpisywanie** wybierz węzeł projektu w **Eksploratora rozwiązań**, a następnie na **projektu** menu, kliknij przycisk **właściwości**. Gdy **projektanta projektu** pojawia się, kliknij przycisk **podpisywanie** kartę.  
  
## <a name="application-and-deployment-manifest-signing"></a>Aplikacji i podpisywanie manifestu wdrożenia  
 **Podpisać manifestów ClickOnce** pole wyboru  
 Zaznacz to pole wyboru, aby podpisać manifestów aplikacji i wdrażania pary kluczy publiczny/prywatny. Aby uzyskać więcej informacji o tym, jak to zrobić, zobacz [porady: logowania aplikacji i manifestów wdrożenia](../../ide/how-to-sign-application-and-deployment-manifests.md).  
  
 **Wybierz z magazynu** przycisku  
 Umożliwia wybranie istniejącego certyfikatu z magazynu certyfikatów osobistych bieżącego użytkownika. Można wybrać jedną z tych certyfikatów do podpisywania manifestów Twojej aplikacji i wdrażania.  
  
 Kliknięcie przycisku **wybierz z magazynu** otwiera **wybierz certyfikat** okno dialogowe, w którym znajduje się lista certyfikatów w osobistym magazynie certyfikatów nie jest prawidłowy (nie wygasł), które mają dostęp do kluczy prywatnych. Cel certyfikatu, którą wybierzesz powinna zawierać podpisywania kodu.  
  
 Jeśli klikniesz przycisk **wyświetlić właściwości certyfikatu**, **szczegóły certyfikatu** zostanie wyświetlone okno dialogowe. To okno dialogowe zawiera szczegółowe informacje o certyfikacie i zawierają dodatkowe opcje. Możesz kliknąć **Dowiedz się więcej o certyfikatach** Aby wyświetlić dodatkowe informacje pomocy.  
  
 **Wybierz z pliku** przycisku  
 Umożliwia wybranie certyfikatu z istniejącego pliku klucza.  
  
 Kliknięcie przycisku **wybierz z pliku** otwiera **wybierz plik** okno dialogowe, w którym można wybrać plik certyfikatu (pfx) klucz. Plik musi być chroniony hasłem i nie może znajdować się już w osobistym magazynie certyfikatów.  
  
 W **wprowadź hasło, aby otworzyć plik** okna dialogowego wprowadź hasło, aby otworzyć plik certyfikatu (pfx) klucza. Informacje o hasło jest przechowywane w listy osobistych kontenera kluczy i w osobistym magazynie certyfikatów.  
  
 **Tworzenie certyfikatu testowego** przycisku  
 Służy do tworzenia certyfikatów do testowania. Certyfikat testowy jest używany do podpisywania manifestów aplikacji i wdrażania ClickOnce.  
  
 Kliknięcie przycisku **utworzyć certyfikatu testu** otwiera **utworzyć certyfikatu testu** okno dialogowe, w którym można wpisać hasło dla pliku klucza silnej nazwy certyfikatu testowego. Plik ma nazwę *projectname*_TemporaryKey.pfx. Jeśli klikniesz przycisk **OK** bez wpisywania hasła, pliku .pfx nie jest hasłem, szyfrowane.  
  
 **Adres URL serwera znaczników czasu** pole  
 Określa adres serwera tego znacznika czasu podpisu. Po podaniu certyfikatu tej witryny zewnętrznej sprawdza czas, który został podpisany aplikacji.  
  
## <a name="assembly-signing"></a>Podpisywanie zestawu  
 **Podpisz zestaw** pole wyboru  
 Zaznacz to pole wyboru, aby podpisać zestaw i utworzyć plik klucza o silnej nazwie. Aby uzyskać więcej informacji na temat podpisywania zestawu za pomocą **projektanta projektu**, zobacz [porady: podpisać zestawu (Visual Studio)](../managing-assembly-and-manifest-signing.md#how-to-sign-an-assembly-in-visual-studio).  
  
 Ta opcja korzysta z narzędzia Al.exe podał [! OBEJMUJĄ[winsdklong](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name).  
  
 **Wybierz plik klucza o silnej nazwie** listy  
 Umożliwia określenie nowego lub istniejącego o silnej nazwie plik klucza używany do podpisywania zestawu. Wybierz  **\<Przeglądaj >** wybierz istniejący plik klucza.  
  
 Wybierz  **\<nowy... >** Aby utworzyć nowy plik klucza do podpisywania zestawu. **Tworzenie silnej nazwy klucza** zostanie wyświetlone okno dialogowe, które można określić nazwę pliku klucza i chronić plik klucza przy użyciu hasła. Hasło musi mieć co najmniej 6 znaków. Jeśli w przypadku określenia hasła, tworzony jest plik wymiany informacji osobistych (pfx); Jeśli hasło nie zostanie określony, zostanie utworzony plik klucza o silnej nazwie (.snk —).  
  
 **Zmień hasło** przycisku  
 Zmienia hasło dla pliku klucza wymiany informacji osobistych (pfx), który jest używany do podpisywania zestawu.  
  
 Kliknięcie przycisku **Zmień hasło** otwiera **Zmień hasło klucza** okno dialogowe. W tym oknie **stare hasło** jest bieżące hasło dla pliku klucza. **Nowe hasło** musi być co najmniej 6 znaków. Informacje o hasło jest przechowywane w magazynie certyfikatów bieżącego użytkownika systemu Windows.  
  
 **Opóźnienie tylko znak** pole wyboru  
 Zaznacz to pole wyboru, aby włączyć podpisywanie opóźnione.  
  
 Należy pamiętać, że opóźnienie podpisanego projektu nie zostaną uruchomione i nie można debugować. Można jednak użyć [Sn.exe (narzędzie silnej nazwy)](/dotnet/framework/tools/sn-exe-strong-name-tool) z `-Vr` opcję pomijania weryfikacji w czasie projektowania.  
  
> [!NOTE]
>  Po zarejestrowaniu zestawu nie zawsze masz dostęp do klucza prywatnego. Na przykład organizacja może być ściśle związany pary kluczy deweloperzy nie mają dostępu do codziennie. Klucz publiczny mogą być dostępne, ale dostęp do klucza prywatnego jest ograniczony do kilku osób. W takim przypadku można użyć *opóźnione* lub *częściowe podpisywanie* zapewnienie klucza publicznego, odkładanie dodanie klucza prywatnego, aż zestaw zostanie przekazany dalej.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do właściwości projektu](../../ide/reference/project-properties-reference.md)   
 [Zarządzanie zestawem i podpisywanie manifestu](../../ide/managing-assembly-and-manifest-signing.md)   
 [Podpisywanie zarządzanych aplikacji silnej nazwy](http://msdn.microsoft.com/en-us/5fef3490-c519-4363-94fd-8b1ad260dab5)   
 [Porady: podpisywanie aplikacji i manifestów wdrożenia](../../ide/how-to-sign-application-and-deployment-manifests.md)   
 [Porady: podpisać zestawu (Visual Studio)](../managing-assembly-and-manifest-signing.md#how-to-sign-an-assembly-in-visual-studio)   
 [Porady: podpisać zestaw o silnej nazwie](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)   
 [Zestawy o silnych nazwach](/dotnet/framework/app-domains/strong-named-assemblies)   