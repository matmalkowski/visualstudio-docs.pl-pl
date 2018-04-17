---
title: Wdrażanie rozwiązania do pakietu Office przy użyciu Instalatora Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, setup project
- Office development in Visual Studio, MSI
- deploying applications [Office development in Visual Studio], setup project
- deploying applications [Office development in Visual Studio], MSI
- ClickOnce deployment [Office development in Visual Studio], MSI
- publishing Office solutions [Office development in Visual Studio], setup project
- Office applications [Office development in Visual Studio], MSI
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f2c51b101b890a2aaf2ea63edfd1f55d05abe18e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="deploying-an-office-solution-by-using-windows-installer"></a>Wdrażanie rozwiązania do pakietu Office przy użyciu Instalatora Windows
Dowiedz się, jak utworzyć Instalatora systemu Windows dla rozwiązań pakietu Office przy użyciu [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  
  
Za pomocą programu Visual Studio, aby utworzyć Instalatora systemu Windows, można wdrożyć rozwiązania do pakietu Office, która wymaga dostępu administracyjnego na komputerze użytkownika końcowego. Na przykład można taki plik zainstalować rozwiązanie tylko raz dla wszystkich użytkowników komputera. Można także wdrożyć rozwiązania do pakietu Office przy użyciu technologii ClickOnce, ale ten rozwiązania należy zainstalować osobno dla każdego użytkownika komputera.  
  
  
## <a name="in-this-topic"></a>W tym temacie:  
  
- [Pobierz przykłady dodatku narzędzi VSTO](#Download)  
  
- [Uzyskać InstallShield Limited Edition](#Obtain)  
  
- [Zdecyduj, jak udzielenia zaufania do rozwiązania](#ApplySecurity)  
  
- [Tworzenie projektu Instalatora](#Create)  
  
- [Dodawanie danych wyjściowych projektu](#Add)  
  
- [Dodaj manifesty wdrażania i aplikacji](#AddD)  
  
- [Konfigurowanie składników zależnych jako wstępnie wymagane składniki](#Configure)  
  
- [Określ, w której chcesz wdrożyć rozwiązanie na komputerze użytkownika](#Location)  
  
- [Konfigurowanie dodatku narzędzi VSTO](#ConfigureRegisitry)  
  
- [Skonfiguruj dostosowania poziomie dokumentu](#ConfigureDocument)  
  
- [Tworzenie projektu Instalatora](#Build)  
  
Aby uzyskać więcej informacji na temat sposobu wdrażania rozwiązania do pakietu Office przy użyciu technologii ClickOnce, zobacz [wdrażania rozwiązania do pakietu Office za pomocą technologii ClickOnce za pomocą](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
Aby uzyskać informacje o sposobie tworzenia pliku Instalatora systemu Windows za pomocą [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)], zobacz [wdrażania programu Visual Studio 2010 Tools dla rozwiązań pakietu Office przy użyciu Instalatora Windows](http://go.microsoft.com/fwlink/?LinkId=201807).  
  
  
## <a name="Download"></a>Pobierz przykłady  
W tym temacie odnosi się do następujących próbek do pobrania.  
  
  
  
|Przykład<br /><br />|Opis<br /><br />|  
|----------|---------------|  
|[ExcelAddIn](http://go.microsoft.com/fwlink/?LinkID=275492)<br /><br />|Dodatek VSTO programu Excel, który można zainstalować na komputerze z systemem 32-bitowy lub 64-bitowej wersji pakietu Office.<br /><br />|  
|[ExcelWorkbook](http://go.microsoft.com/fwlink/?LinkID=275493)<br /><br />|Dostosowanie poziomie dokumentu programu Excel, które można zainstalować na komputerze z systemem 32-bitowy lub 64-bitowej wersji pakietu Office.<br /><br />|  
  
## <a name="ApplySecurity"></a>Zdecyduj, jak udzielenia zaufania do rozwiązania  
Aby rozwiązanie było uruchomić na komputerach użytkowników, należy udzielić zaufania w jednym z następujących sposobów lub użytkownicy muszą odpowiadać na wiersz zaufania przy instalacji rozwiązania.  
  
  
- Podpisać manifestów za pomocą certyfikatu, który identyfikuje znanego i zaufanego wydawcy. Aby uzyskać więcej informacji, zobacz [ufające rozwiązania przez podpisywanie aplikacji i manifestów wdrożenia](../vsto/granting-trust-to-office-solutions.md#Signing).  
  
- Zainstaluj rozwiązania do katalogu plików programu na komputerze użytkownika.  
  
> [!NOTE]  
> Dostosowywanie na poziomie dokumentu Lokalizacja dokumentu również musi być zaufany. Aby uzyskać więcej informacji, zobacz [udzielanie zaufania do dokumentów](../vsto/granting-trust-to-documents.md).  
  
  
## <a name="Obtain"></a>Uzyskać InstallShield Limited Edition  
Plik Instalatora Windows można utworzyć przy użyciu InstallShield Limited Edition (Wyspa), która jest bezpłatne, jeśli po zainstalowaniu programu Visual Studio. Wyspa zastępuje funkcjonalność szablony projektów instalacji i wdrażania, które oferowane poprzednich wersji programu Visual Studio.  
  
  
#### <a name="to-get-installshield-limited-edition"></a>Aby uzyskać InstallShield Limited Edition  
  
1. Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
   **Nowy projekt** zostanie otwarte okno dialogowe.  
  
2. W okienku szablonów rozwiń **inne typy projektów**, a następnie wybierz pozycję **instalacji i wdrażania** szablonu.  
  
3. Na liście typów projektów dla **instalacji i wdrażania**, wybierz **Włącz InstallShield Limited Edition**, a następnie wybierz pozycję **OK** przycisku.  
  
   Zostanie wyświetlona strona zawierająca informacje o tym, jak uzyskać InstallShield Limited Edition.  
  
4. Na tej stronie wybierz **przejdź do witryny sieci web pobierania** łącza.  
  
5. Na stronie pobierania InstallShield Limited Edition, wprowadź wymagane informacje w odpowiednich polach, a następnie wybierz pozycję **Pobierz teraz** łącza.  
  
   Po pobraniu, instalowania i aktywowania produktu, **InstallShield Limited Edition projektu** szablon jest wyświetlany w programie Visual Studio.  
  
  
## <a name="Create"></a>Tworzenie projektu Instalatora  
  
####   
1. W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], otwórz projekt pakietu Office, który chcesz wdrożyć.  
  
   Przykłady dodatku VSTO, które są skojarzone z tym temacie zawiera projektu o nazwie **ExcelAddIn**. Przykłady dostosowania na poziomie dokumentu zawiera projektu o nazwie **ExcelWorkbook**. W tym temacie będzie odnosić się do pakietu Office projektu w rozwiązaniu przy użyciu jednej z tych dwóch nazw.  
  
2. Na pasku menu wybierz **pliku**, **Dodaj**, **nowy projekt**.  
  
   **Dodawanie nowego projektu** zostanie otwarte okno dialogowe.  
  
3. W okienku szablonów rozwiń **inne typy projektów**, a następnie wybierz pozycję **instalacji i wdrażania** szablonu.  
  
4. Na liście typów projektów dla **instalacji i wdrażania**, wybierz **InstallShield Limited Edition projektu**, nazwij projekt, a następnie wybierz **OK** przycisku.  
  
   Nowo utworzony projekt instalatora InstallShield pojawia się w rozwiązaniu.  
  
   Przykłady dla tego tematu zawierają instalacji projektu o nazwie **OfficeAddInSetup**. W tym temacie będzie odnosić się do konfiguracji projektu w rozwiązaniu przy użyciu tej samej nazwie.  
  
  
## <a name="Add"></a>Dodawanie danych wyjściowych projektu  
Możesz skonfigurować **OfficeAddInSetup** projektu, aby dołączyć dane wyjściowe projektu pakietu Office. Dla projektów dodatku VSTO danych wyjściowych projektu jest tylko zestawu rozwiązania. Dla projektów dostosowania na poziomie dokumentu dane wyjściowe projektu zawiera nie tylko zestawu rozwiązania, ale także samego dokumentu.  
  
  
#### <a name="to-add-the-project-output"></a>Można dodać danych wyjściowych projektu  
  
1. W **Eksploratora rozwiązań**, rozwiń węzeł **OfficeAddInSetup** węzła projektu, a następnie wybierz **Asystentem projektu** pliku, który na poniższej ilustracji przedstawiono.  
  
   ![Asystent pliku w Eksploratorze rozwiązań projektu](../vsto/media/installshield-projectassistant.png "projektu Asystenta plików w Eksploratorze rozwiązań")  
  
2. Na pasku menu wybierz **widoku**, **Otwórz**.  
  
3. W dolnej części **Asystent projektu** wybierz pozycję **pliki aplikacji** przycisku, który na poniższej ilustracji przedstawiono.  
  
   ![Przycisk pliki aplikacji. ] (../vsto/media/installshield-applicationfiles.png "Przycisk pliki aplikacji.")  
  
4. W **pliki aplikacji** wybierz pozycję **dodać danych wyjściowych projektu** przycisku.  
  
5. W **selektora danych wyjściowych w usłudze Visual Studio** okno dialogowe, wybierz opcję **główny wynik** pole wyboru, a następnie wybierz pozycję **OK** przycisku.  
  
  
## <a name="AddD"></a>Dodaj manifesty wdrażania i aplikacji  
  
####   
1. W **pliki aplikacji** wybierz pozycję **Dodaj pliki** przycisku.  
  
2. W **Otwórz** okno dialogowe, przejdź do katalogu wyjściowego **ExcelAddIn** projektu.  
  
   Zwykle katalog wyjściowy jest **bin\release** podfolder katalog główny projektu, w zależności od wybranej konfiguracji kompilacji.  
  
3. Wybierz katalog wyjściowy **ExcelAddIn.vsto** i **ExcelAddIn.dll.manifest** pliki, a następnie wybierz pozycję **Otwórz** przycisku.  
  
   **Pliki aplikacji** strona zawiera teraz pliku wyjściowego projektu, manifest wdrażania i manifest aplikacji, jak przedstawiono na poniższej ilustracji.  
  
   ![Pliki wyjściowe projektu Instalatora. ] (../vsto/media/installshield-outputfiles.png "Plików wyjściowych projektu Instalatora.")  
  
  
## <a name="Configure"></a>Konfigurowanie składników zależnych jako wstępnie wymagane składniki  
W konfiguracji aplikacji musi zawierać nie tylko następujące składniki, ale także inne składniki, które są wymagane do rozwiązania do uruchomienia.  
  
  
- Wersja programu .NET Framework który celów rozwiązania pakietu Office.  
  
- Microsoft Visual Studio 2010 Tools for Office Runtime.  
  
  
### <a name="add-the-net-framework-4-or-the-net-framework-45-as-a-prerequisite"></a>Dodaj jako warunek wstępny programu .NET Framework 4 lub .NET Framework 4.5  
  
#####   
1. W **Eksploratora rozwiązań**, rozwiń węzeł **OfficeAddInSetup** węzła projektu, rozwiń **Określ dane aplikacji** węzeł, a następnie wybierz pozycję  **Pakiety redystrybucyjne** pliku, który na poniższej ilustracji przedstawiono.  
  
   ![Plik pakietów redystrybucyjnych w Eksploratorze rozwiązań](../vsto/media/installshield-redistributablesfile.png "plików pakietów redystrybucyjnych w Eksploratorze rozwiązań")  
  
2. Na pasku menu wybierz **widoku**, **Otwórz**.  
  
   **Pakietów redystrybucyjnych** zostanie otwarta strona.  
  
3. Na liście składników do dystrybucji, wybierz odpowiednie pole wyboru dla używanej wersji programu .NET Framework który celów rozwiązania.  
  
   Na przykład jeśli elementy docelowe rozwiązanie [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], wybierz pozycję **Microsoft .NET Framework 4.5 Full** pole wyboru. Mogą być wyświetlane okno dialogowe z pytaniem, czy chcesz zainstalować składnik redystrybucyjny co InstallShield wymaga, aby dodać składnik jako warunek wstępny. Jeśli nie zostanie wyświetlone okno dialogowe, składnik już istnieje na tym komputerze.  
  
4. Jeśli zostanie wyświetlone okno dialogowe, wybierz **nr** przycisku.  
  
  
### <a name="AddToolsForOffice"></a>Dodaj Visual Studio 2010 Tools for Office Runtime  
**Pakietów redystrybucyjnych** strona zawiera element o nazwie **Microsoft VSTO 2010 Runtime**, ale odwołuje się do starszej wersji środowiska uruchomieniowego. W związku z tym należy ręcznie utworzyć plik konfiguracji, który odwołuje się do najnowszej wersji. Następnie możesz umieścić plik w tym samym katalogu co pliki konfiguracji dla wszystkich innych elementów, które są widoczne w **pakietów redystrybucyjnych** strony.  
  
  
##### <a name="to-add-the-visual-studio-2010-tools-for-office-runtime-as-a-prerequisite"></a>Aby dodać Visual Studio 2010 Tools for Office Runtime jako warunek wstępny  
  
1. Otwórz Notatnik, a następnie wklej następujący kod XML w pliku tekstowym.  
  
  
   ```xml  
   <?xml version="1.0" encoding="UTF-8"?>  
   <SetupPrereq>  
   <conditions>  
       <condition Type="32" Comparison="2" Path="HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSTO Runtime Setup\v4R" FileName="Version" ReturnValue="10.0.50903" Bits="2"></condition>  
   <condition Type="32" Comparison="2" Path="HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4R" FileName="Version" ReturnValue="10.0.50903" Bits="2"></condition>  
   </conditions>  
   <files>  
       <file LocalFile="<ISProductFolder>\SetupPrerequisites\VSTOR\vstor_redist.exe" URL="http://download.microsoft.com/download/C/0/0/C001737F-822B-48C2-8F6A-CDE13B4B9E9C/vstor_redist.exe" CheckSum="88b8aa9e8c90818f98c80ac4dd998b88" FileSize=" 0,40117912"></file>  
   </files>  
   <execute file="vstor_redist.exe" returncodetoreboot="1641,3010" requiresmsiengine="1">  
   </execute>  
   <properties Id="{15965040-56BB-49B8-A88F-3525C48D9BA8}" Description="This prerequisite installs the most recent version of the Microsoft Visual Studio 2010 Tools for Office Runtime." >  
   </properties>  
     
   </SetupPrereq>  
   ```  
  
2. Generuj identyfikator GUID w programie Visual Studio. Na **narzędzia** menu, wybierz **utworzyć identyfikatora GUID**.  
  
3. W **GUID generator** programowania, wybierz **Format rejestru** przycisk opcji, wybierz **kopiowania** przycisk, a następnie wybierz pozycję **zakończenia** przycisk.  
  
4. W programie Notatnik, Zastąp tekst **swój identyfikator GUID tu** przez wklejenie identyfikator GUID w jego miejscu.  
  
   **&lt;Właściwości&gt;** element pliku jest podobny do następującego.  
  
  
   ```xml  
   <properties Id="{87989B73-21DC-4403-8FD1-0C68A41A6D8C}" Description="This prerequisite installs the most recent version of the Microsoft Visual Studio 2010 Tools for Office Runtime." >  
   </properties>  
   ```  
  
5. Na pasku menu w Notatniku wybierz **pliku**, **zapisać**.  
  
6. W **Zapisz jako** okno dialogowe, przejdź do Twojej **pulpitu** folderu.  
  
7. W **Zapisz jako typ** wybierz **wszystkie pliki (&#42;.&#42;)** .  
  
8. W **nazwę pliku** wprowadź **programu Visual Studio 2010 Tools dla pakietu Office Runtime.prq**, a następnie wybierz pozycję **zapisać** przycisku.  
  
   > [!NOTE]  
   >    Upewnij się, że możesz dodać **.prq** na końcu nazwy pliku, aby zidentyfikować ten plik jako plik wymagań wstępnych.  
  
9. Zamknij Notatnik.  
  
10. Z sieci **pulpitu** folder, skopiuj Visual Studio 2010 Tools dla pakietu Office Runtime.prq pliku do jednego z następujących katalogów na tym komputerze.  
  
   Dla 32-bitowe systemy operacyjne: %ProgramFiles%\InstallShield\2013LE\SetupPrerequisites\  
  
   64-bitowe systemy operacyjne: % ProgramFiles (x86) %\2013LE\SetupPrerequisites\  
  
11. W **Redistributable** strony projektu InstallShield wybierz **Odśwież** przycisk, aby odświeżyć listę składników do dystrybucji, jak przedstawiono na poniższej ilustracji.  
  
   ![Przycisk Odśwież. ] (../vsto/media/installshield-refreshbutton.png "Przycisk Odśwież.")  
  
12. Na liście składników do dystrybucji, wybierz **Visual Studio 2010 Tools for Office Runtime** pole wyboru.  
  
   Okno dialogowe może wyglądać pytaniem, czy chcesz zainstalować składnik redystrybucyjny. Jeśli nie zostanie wyświetlone okno dialogowe, możesz przejść do [Określ, w której chcesz wdrożyć rozwiązanie na komputerze użytkownika](#Location) tego tematu.  
  
13. Jeśli zostanie wyświetlone okno dialogowe, wybierz **nr** przycisku.  
  
  
## <a name="Location"></a>Określ, gdzie chcesz zainstalować rozwiązania na komputerze użytkownika  
  
####   
1. W **Eksploratora rozwiązań**, rozwiń węzeł **OfficeAddInSetup** węzła, rozwiń węzeł **organizowanie konfigurację** węzła, a następnie wybierz **informacjeogólne** pliku.  
  
2. Na pasku menu wybierz **widoku**, **Otwórz**.  
  
3. Na liście właściwości, wybierz **Przeglądaj** znajdujący się obok **INSTALLDIR** właściwości.  
  
4. W **ustawić INSTALLDIR** oknie dialogowym Wybierz folderu na komputerze użytkownika, w którym chcesz zainstalować rozwiązania.  
  
   > [!NOTE]  
   >    Można również utworzyć podkatalogi w **ustawić INSTALLDIR** okno dialogowe Otwieranie menu skrótów dla każdego folderu w liście.  
  
  
## <a name="ConfigureRegisitry"></a>Konfigurowanie dodatku narzędzi VSTO  
Można określić, czy mają dodatek VSTO do zainstalowania dla wszystkich użytkowników komputera (na komputer) lub tylko dla użytkownika, przeprowadzanie instalacji (użytkownika).  
  
Do obsługi instalacji na komputerze, należy utworzyć dwa oddzielne pliki instalacyjne. Można podzielić programy instalacyjne oparte na wersji pakietu Office (32-bitowe i 64-bitowe) lub na wersji systemu Windows (32-bitowe i 64-bitowe) z systemem użytkownika.  
  
Instalacje użytkownika wymagają tylko jeden Instalator niezależnie od wersji pakietu Office lub systemu Windows.  
  
> [!NOTE]  
> Ta sekcja dotyczy tylko wtedy, gdy jest wdrażany w dodatku VSTO. Jeśli wdrażasz dostosowania poziomie dokumentu można od razu przejść do [skonfigurować dostosowania poziomie dokumentu](#ConfigureDocument) sekcji.  
  
  
#### <a name="to-specify-whether-you-want-to-support-per-user-or-per-computer-installations"></a>Aby określić, czy obsługuje instalacji dla poszczególnych użytkowników lub komputerów  
  
1. W **Eksploratora rozwiązań**, rozwiń węzeł **OfficeAddInSetup** węzła projektu, rozwiń **organizowanie Your Instalatora** węzła, a następnie wybierz **informacje ogólne**  pliku.  
  
2. Na pasku menu wybierz **widoku**, **Otwórz**.  
  
   Właściwości projektu Instalatora są wyświetlane.  
  
3. Na liście **AllUSERS** właściwości, określ, czy to rozwiązanie ma zostać zainstalowany dla wszystkich użytkowników komputera lub użytkownika, który instaluje rozwiązanie.  
  
   Aby zainstalować dodatku VSTO dla bieżącego użytkownika, wybierz **ALLUSERS = "" (Instalacja na użytkownika)**. Aby zainstalować dodatku VSTO dla wszystkich użytkowników komputera, wybierz **ALLUSERS = 1 (Instalacja dla poszczególnych komputerów)**  
  
   W następnej procedurze utworzysz klucze rejestru, aby umożliwić aplikacji pakietu Office odnaleźć i załadować dodatku VSTO. Zobacz [wpisy rejestru dotyczące dodatków VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
  
#### <a name="to-create-registry-keys"></a>Do tworzenia kluczy rejestru  
  
1. W **Eksploratora rozwiązań**, wybierz **Asystentem projektu** węzła.  
  
   Na pasku menu wybierz **widoku**, **Otwórz**.  
  
2. W dolnej części **Asystent projektu** wybierz pozycję **rejestru aplikacji** przycisku, który na poniższej ilustracji przedstawiono.  
  
   ![Przycisk rejestru na komputerze. ] (../vsto/media/installshield-applicationregistry.gif "Przycisk rejestru na komputerze.")  
  
   **Rejestru aplikacji** zostanie wyświetlona strona.  
  
3. W obszarze **chcesz skonfigurować dane rejestru, który zainstaluje aplikację?**, wybierz **tak** przycisk opcji.  
  
4. W **widoku rejestru komputera docelowego** liście, Dodaj klucza hierarchii, które umożliwia typu Instalatora, w którym chcesz utworzyć.  
  
   Ścieżkę, którą można skonfigurować w tej sekcji zależy od tego, czy utworzyć Instalatora dla poszczególnych użytkowników lub Instalatora na komputerze.  
  
   **Instalator na użytkownika**  
  
   **HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**  
  
   **Instalatorzy na komputerze, na podstawie wersji pakietu Office**  
  
  
  
|Wersja pakietu Office<br /><br />|Ścieżka konfiguracyjna InstallShield<br /><br />|  
|------------------|------------------------------------|  
|32-bitowa<br /><br />|**HKEY_LOCAL_MACHINE\Software(32-bit) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br />|  
|64-bitowy<br /><br />|**HKEY_LOCAL_MACHINE\Software(64-bit) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br />|  
   **Instalatorzy na komputerze, na podstawie wersji systemu Windows**  
  
  
  
|Wersja systemu Windows<br /><br />|Ścieżka konfiguracyjna InstallShield<br /><br />|  
|-------------------|------------------------------------|  
|32-bitowa<br /><br />|**HKEY_LOCAL_MACHINE\Software(32-bit) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br />|  
|64-bitowy<br /><br />|**HKEY_LOCAL_MACHINE\Software(32-bit) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br />**HKEY_LOCAL_MACHINE\Software(64-bit) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br />|  
   > [!NOTE]  
   >    Instalatora dla 64-bitowego systemu Windows wymaga dwóch ścieżek rejestru, ponieważ umożliwiające użytkownikom na uruchamianie 32-bitowe i 64-bitowej wersji pakietu Office na komputerze z systemem 64-bitowym systemie Windows.  
  
   > [!NOTE]  
   >    Najlepszym rozwiązaniem rozpoczynać nazwę użytkownika dodatku VSTO nazwę swojej firmy. Tę Konwencję zwiększa prawdopodobieństwo, że klucz będzie unikatowa i zmniejsza ryzyko wystąpienia konfliktu z dodatku VSTO z innego dostawcy. Dodatków, które mają taką samą nazwę na przykład zastąpić klucze rejestracji siebie nawzajem. Tej metody nie może zagwarantować, że klucz jest unikatowa, ale można ograniczyć potencjalne konflikty nazw.  
  
5. Po utworzeniu hierarchii z kluczy, otwórz menu skrótów **SampleCompany.ExcelAddIn** klucza, wybierz **nowy**, a następnie wybierz pozycję **wartość ciągu**.  
  
   Nową wartość ciągu jest wyświetlany w **dane rejestru komputera docelowego** listy. Nazwa wartości ciągu zostanie wyróżniona, dzięki czemu można zmienić jego nazwę.  
  
6. Zmień nazwę wartości **opis**.  
  
7. Powtórz ten proces, aby utworzyć następujące wartości.  
  
  
  
|Typ wartości<br /><br />|Nazwa<br /><br />|  
|--------------|--------|  
|Wartość ciągu<br /><br />|**friendlyName**<br /><br />|  
|Wartość DWORD<br /><br />|**LoadBehavior**<br /><br />|  
|Wartość ciągu<br /><br />|**Manifest**<br /><br />|  
  
8. Otwórz menu skrótów **opis** wartość, a następnie wybierz pozycję **Modyfikuj**.  
  
   **Edytowanie danych** zostanie wyświetlone okno dialogowe.  
  
9. W **dane wartości** tekst wprowadź **Excel pokaz Add-In**, a następnie wybierz pozycję **OK** przycisku.  
  
   Ten opis jest wyświetlany, gdy użytkownik otwiera aplikację pakietu Office, otwiera **opcje** okno dialogowe, a następnie w **Add-Ins** okienku wybierze dodatku VSTO.  
  
10. Otwórz menu skrótów **FriendlyName** wartość, a następnie wybierz pozycję **Modyfikuj**.  
  
   **Edytowanie danych** zostanie wyświetlone okno dialogowe.  
  
11. W **dane wartości** tekst wprowadź **Excel pokaz Add-In**, a następnie wybierz pozycję **OK** przycisku.  
  
   Ten ciąg jest wyświetlana w **dodatki COM** okno dialogowe w aplikacji pakietu Office. Domyślnie wartość ciągu jest identyfikatorem dodatku narzędzi VSTO  
  
12. Otwórz menu skrótów **LoadBehavior** wartość, a następnie wybierz pozycję **Modyfikuj**.  
  
   **Edytowanie danych** zostanie wyświetlone okno dialogowe.  
  
13. W **dane wartości** tekst wprowadź **3**, a następnie wybierz pozycję **OK** przycisku.  
  
   Wartość 3 ładuje dodatku VSTO podczas uruchamiania aplikacji. Aby uzyskać więcej informacji na temat LoadBehavior wartości, zobacz [wpisy rejestru dotyczące dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
14. Otwórz menu skrótów **manifestu** wartość, a następnie wybierz pozycję **Modyfikuj**.  
  
   **Edytowanie danych** zostanie wyświetlone okno dialogowe.  
  
15. W **dane wartości** tekst wprowadź **file:///[INSTALLDIR]ExcelAddIn.vsto|vstolocal**, a następnie wybierz pozycję **OK** przycisku.  
  
   Visual Studio 2010 Tools for Office Runtime używa tej ścieżki, aby zlokalizować manifest wdrażania. **[INSTALLDIR]** część ta ścieżka jest makra, który jest mapowany na **INSTALLDIR** właściwości w **ogólne informacje** strony właściwości projektu instalatora InstallShield. Ta właściwość określa lokalizację na komputerze docelowym, aby zainstalować dodatku VSTO. **| Vstolocal** sufiks gwarantuje, że rozwiązanie jest ładowany z folderu instalacji, a nie pamięci podręcznej ClickOnce.  
  
> [!IMPORTANT]  
> Jeśli tworzysz regionu formularza niestandardowego w dodatku VSTO dla programu Outlook, należy utworzyć więcej wpisów rejestru do zarejestrowania obszaru z programu Outlook. Aby uzyskać więcej informacji, zobacz [wpisy rejestru dotyczące regionów formularzy programu Outlook](../vsto/registry-entries-for-vsto-add-ins.md#OutlookEntries).  
  
  
## <a name="ConfigureDocument"></a>Skonfiguruj dostosowania poziomie dokumentu  
Ta sekcja dotyczy tylko wtedy, gdy jest wdrażany dostosowania poziomie dokumentu. W przypadku instalowania dodatku VSTO, można przejść bezpośrednio do [kompilacji projektu Instalatora](#Build) sekcji.  
  
Dostosowywanie na poziomie dokumentu nie używaj kluczy rejestru. Zamiast tego niestandardowe właściwości dokumentu zawiera lokalizacja manifestu rozmieszczenia.  
  
Aby zmodyfikować właściwości niestandardowe, należy utworzyć program, który usuwa dostosowania dokumentu na poziomie dokumentu, modyfikuje odpowiednie właściwości i ponownie dołącza dostosowania do dokumentu. Następnie można utworzyć akcji niestandardowej, która uruchamia program, a ta akcja jest dodawanie do projektu Instalatora.  
  
  
#### <a name="to-create-a-program-that-modifies-document-properties"></a>Aby utworzyć program, który modyfikuje właściwości dokumentu  
  
1. Na pasku menu wybierz **pliku**, **Dodaj**, **nowy projekt**.  
  
   **Dodawanie nowego projektu** zostanie wyświetlone okno dialogowe.  
  
2. W okienku szablonów w węźle dla języka, którego chcesz użyć, wybierz **Windows** folderu.  
  
3. Na liście typów projektów dla **Windows**, wybierz **aplikacji konsoli** szablonu.  
  
4. Nazwij projekt **SetExcelDocumentProperties**, a następnie wybierz pozycję **OK** przycisku.  
  
5. W **Eksploratora rozwiązań**, wybierz **Pokaż wszystkie pliki** przycisku, otwórz menu skrótów **SetExcelDocumentProperties** węzła projektu, a następnie wybierz **Dodaj odwołanie**.  
  
6. W **Menedżera odwołań** oknie dialogowym wybierz **rozszerzenia** karcie, a następnie zaznacz pole wyboru obok następujące zestawy, a następnie wybierz **OK** przycisku.  
  
  
   - Microsoft.VisualStudio.Tools.Applications.Runtime  
  
   - Microsoft.VisualStudio.Tools.Applications.ServerDocument  
  
7. W **Eksploratora rozwiązań**, wybierz **Program.cs** pliku (w przypadku aplikacji C#) lub **Module1.vb** pliku (dla aplikacji Visual Basic).  
  
8. Na pasku menu wybierz **widoku**, **Otwórz**.  
  
9. Zastąp zawartość całego pliku następującym kodem.  
  
[!code-vb[Trin_CustomAction#1](../vsto/codesnippet/VisualBasic/setexceldocumentproperties/module1.vb#1)]
[!code-csharp[Trin_CustomAction#1](../vsto/codesnippet/CSharp/setexceldocumentproperties/program.cs#1)]  
  
10. Skompiluj projekt.  
  
  
#### <a name="to-add-a-custom-action-that-runs-your-program"></a>Aby dodać akcji niestandardowej, która uruchamia program  
  
1. W **Eksploratora rozwiązań**, rozwiń węzeł **OfficeAddInSetup** węzła projektu, a następnie wybierz **Asystentem projektu** pliku, który na poniższej ilustracji przedstawiono.  
  
   ![Asystent pliku w Eksploratorze rozwiązań projektu](../vsto/media/installshield-projectassistant.png "projektu Asystenta plików w Eksploratorze rozwiązań")  
  
2. Na pasku menu wybierz **widoku**, **Otwórz**.  
  
3. W dolnej części **Asystent projektu** wybierz pozycję **pliki aplikacji** przycisku, który na poniższej ilustracji przedstawiono.  
  
   ![Przycisk pliki aplikacji. ] (../vsto/media/installshield-applicationfiles.png "Przycisk pliki aplikacji.")  
  
4. W **pliki aplikacji** wybierz pozycję **dodać danych wyjściowych projektu** przycisku.  
  
   **Selektora danych wyjściowych w usłudze Visual Studio** zostanie wyświetlone okno dialogowe.  
  
5. W obszarze **SetExcelDocumentProperties** węzła, wybierz opcję **główny wynik** pole wyboru, a następnie wybierz pozycję **OK** przycisku.  
  
6. W **Eksploratora rozwiązań**w obszarze **OfficeAddInSetup** węzła, rozwiń węzeł **zdefiniować wymagania dotyczące konfiguracji i akcji** węzła, a następnie wybierz pozycję **niestandardowe Akcje** folderu.  
  
7. Na pasku menu wybierz **widoku**, **Otwórz**.  
  
   Lista zdarzeń są wyświetlane w okienku na stronie ekranu.  
  
   > [!NOTE]  
   >    Tylko kilka zdarzeń, które są wyświetlane na tej liście są dostępne w InstallShield Limited Edition. W tej procedurze uruchomisz program przy użyciu **po instalacji pełnego powodzenia w oknie dialogowym** zdarzeń.  
  
8. Na liście zdarzeń w obszarze **akcje niestandardowe podczas instalacji**, otwórz menu skrótów **po instalacji pełnego powodzenia w oknie dialogowym** zdarzeń, a następnie wybierz pozycję **nowego pliku EXE**.  
  
   Akcja niestandardowa o nazwie **NewCustomAction1** jest wyświetlany w obszarze **po instalacji pełnego powodzenia w oknie dialogowym** zdarzeń. Zestaw właściwości dla akcji niestandardowej zostanie wyświetlony w okienku obok zdarzenia.  
  
   > [!IMPORTANT]  
   >    Dwa **po instalacji pełnego powodzenia w oknie dialogowym** zdarzenia są wyświetlane na liście zdarzeń. Upewnij się, że wybrano wystąpienie **po instalacji pełnego powodzenia w oknie dialogowym** zdarzeń, który jest wyświetlany w obszarze **akcje niestandardowe podczas instalacji** węzła.  
  
9. Na liście **lokalizacji źródłowej** właściwości, wybierz **instalowane wraz z produktem**.  
  
10. Wybierz **Przeglądaj** znajdujący się obok **nazwę pliku** właściwości.  
  
11. W **Przeglądaj w poszukiwaniu pliku docelowego** okno dialogowe, przejdź do **SetExcelDocumentProperties.Primary.output** pliku, a następnie wybierz pozycję **Otwórz** przycisku.  
  
   Lokalizacja tego pliku zależy od określonej dla folderu **INSTALLDIR** właściwości projektu Instalatora. Na przykład, jeśli wartość tej właściwości do folderu o nazwie **DemoWorkbookApp [PersonalFolder]**, można znaleźć **SetExcelDocumentProperties.Primary.output** plików, przechodząc do **[ \DemoWorkbookApp ProgramFilesFolder]**.  
  
   W następnych kilku krokach możesz pobrać identyfikator rozwiązania dokumentu i następnie przekazać ten identyfikator jako parametr do aplikacji konsoli. Będzie także podać lokalizację dokumentu, manifest wdrażania i zestawu dokumentu.  
  
12. Otwórz menu skrótów **ExcelWorkbook** projektu, a następnie wybierz pozycję **Otwórz Folder w Eksploratorze Windows** lub **Otwórz Folder w Eksploratorze plików** w zależności od tego, czy Twoje działania System.  
  
   Otwiera folder zawierający rozwiązania.  
  
13. Otwórz plik projektu rozwiązania w Notatniku. Projekty Visual Basic nazwa pliku jest ExcelWorkbook.vbproj. Dla projektów C# nazwa pliku jest ExcelWorkbook.csproj.  
  
14. W pliku projektu, wyszukaj **&lt;SolutionID&gt;** elementu, skopiuj wartość do Schowka, a następnie zamknij Notatnik.  
  
   Tę wartość należy przekazać do aplikacji konsoli jako parametr.  
  
15. Na stronie właściwości **NewCustomAction1**ustaw **wiersza polecenia** właściwości następujący wiersz tekstu.  
  
  
   ```  
   /assemblyLocation="[INSTALLDIR]ExcelWorkbook.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbook.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbook.xlsx" /solutionID="Your Solution ID"  
   ```  
  
16. Zastąp **swój identyfikator rozwiązania** o identyfikatorze rozwiązania, który został skopiowany do Schowka.  
  
   > [!IMPORTANT]  
   >    Test z Instalatora, aby sprawdzić, czy aplikacja konsolowa, która jest uruchamiana ta akcja może uzyskiwać dostęp do dokumentów w katalogu [INSTALLDIR]. Niektóre katalogów znajdujących się na komputerze użytkownika mogą wymagać dostępu administracyjnego (na przykład katalog Program Files). Czy w przypadku wdrażania rozwiązania w katalogu, który wymaga dostępu administracyjnego, należy otworzyć **właściwości** okno dialogowe plik setup.exe, wybierz **zgodności** , a następnie wybierz **uruchomić ten program jako administrator** pole wyboru przed rozpoczęciem dystrybucji Instalatora. Jeśli nie chcesz, aby użytkownikom na uruchamianie programu instalacyjnego z uprawnieniami administracyjnymi, ustaw właściwość [INSTALLDIR] do katalogu, do której użytkownik prawdopodobnie ma dostęp, takich jak **dokumenty** katalogu. Aby uzyskać więcej informacji, zobacz [Określ, gdzie chcesz zainstalować rozwiązanie na komputerze użytkownika](#Location) tego tematu.  
  
  
## <a name="Build"></a>Tworzenie projektu Instalatora  
  
####   
1. W **Eksploratora rozwiązań**, rozwiń węzeł **przygotowania do wydania** węzeł, a następnie wybierz pozycję **wersje** pliku.  
  
2. Na pasku menu wybierz **widoku**, **Otwórz**.  
  
   **Kompilacje** zostanie otwarty Eksplorator w okienku po stronie, w którym można wybrać typ zlecenia, który chcesz utworzyć.  
  
3. W **kompilacje** explorer, wybierz **SingleImage** folderu.  
  
4. W okienku dalej, aby **kompilacje** explorer, wybierz **Setup.exe** kartę.  
  
5. W **Setup.exe** stronę właściwości z **InstallShield wymagania wstępne dotyczące lokalizacji** wybierz **pobieranie z sieci Web**.  
  
6. Na pasku menu wybierz **kompilacji**, **programu Configuration Manager**.  
  
7. W **aktywnej konfiguracji rozwiązania** wybierz **SingleImage**.  
  
8. W **projektu kontekstów** tabeli w **konfiguracji** kolumny **OfficeAddInSetup** projektu, wybierz **SingleImage**, a następnie Wybierz **Zamknij** przycisku.  
  
9. Na pasku menu wybierz **kompilacji**, **kompilacji OfficeAddInSetup**.  
  
   Po zakończeniu kompilacji, można znaleźć pliku setup.exe z **OfficeAddInSetup** projektu w następującej lokalizacji: *OfficeAddInSetupProjectRoot *** \OfficeAddInSetup\Express\SingleImage\DiskImages\ DYSK 1\**  
  
  
## <a name="see-also"></a>Zobacz też  
[Wymagania wstępne rozwiązania pakietu Office dla wdrożenia](http://msdn.microsoft.com/en-us/library/9f672809-43a3-40a1-9057-397ce3b5126e)  
[Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)  
[Wpisy rejestru dotyczące dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md)  
[Niestandardowe właściwości dokumentu — omówienie](../vsto/custom-document-properties-overview.md)  
[Udzielanie zaufania do rozwiązań pakietu Office](../vsto/granting-trust-to-office-solutions.md)  
[Udzielanie zaufania do dokumentów](../vsto/granting-trust-to-documents.md)  
[Wdrażanie programu Visual Studio 2010 Tools dla rozwiązań pakietu Office za pomocą Instalatora Windows](http://go.microsoft.com/fwlink/?LinkId=201807)  
  
