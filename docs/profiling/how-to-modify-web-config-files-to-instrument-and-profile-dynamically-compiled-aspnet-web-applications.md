---
title: 'Porady: modyfikowanie plików Web.Config w celu Instrumentowania i profilowania dynamicznie skompilowanych aplikacji sieci Web ASP.NET | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: a92e5692-2183-4ae3-9431-b067c6a7aab4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 427a0d0de82ba5957422fdd9b2db6067ece2f4f8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-modify-webconfig-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications"></a>Porady: modyfikowanie plików Web.Config w celu instrumentowania i profilowania dynamicznie skompilowanych aplikacji sieci ASP.NET
Można użyć [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] skompilowane metody Instrumentacji w narzędziach profilowania do zbierania danych o chronometrażu, dane alokacji pamięci .NET i .NET danych o okresie istnienia obiektu z dynamicznie [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web.  
  
 W tym temacie opisano sposób modyfikowania plik konfiguracji web.config w celu umożliwienia Instrumentacja i profilowanie [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web.  
  
> [!NOTE]
>  Nie musisz zmodyfikować plik web.config, gdy używasz metoda profilowania próbkowania lub Instrumentacja wstępnie skompilowanym [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] modułu.  
  
 Główny plik web.config jest **konfiguracji** elementu. Instrumentacja i profilowania dynamicznie skompilowanych [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] sieci Web aplikacji, musisz dodać lub zmodyfikować następujące elementy:  
  
-   A **konfiguracji/runtime/assemblybinding — / dependentAssembly** element, który identyfikuje zestaw Microsoft.VisualStudio.Enterprise.ASPNetHelper kontrolujące profilowania. **DependentAssembly** element zawiera dwa elementy podrzędne: **assemblyIdentity** i **codeBase**.  
  
-   A **configuration/system.web/compilation** element, który identyfikuje kroku kompilacji po przetwarzaniu profilera dla zestawu docelowego.  
  
-   Dwa **dodać** elementy, które identyfikują lokalizację narzędzi profilowania są dodawane do **konfiguracji/appSettings** sekcji.  
  
 Firma Microsoft zaleca, aby utworzyć kopię oryginalnego pliku web.config, który można przywrócić konfigurację aplikacji.  
  
### <a name="to-add-the-aspnethelper-assembly-as-a-configurationruntimeassemblybindingdependentassembly-element"></a>Aby dodać zestaw ASPNetHelper jako elementu konfiguracji/runtime/assemblybinding — / dependentAssembly  
  
1.  W razie potrzeby dodaj **środowiska uruchomieniowego** element jako element podrzędny elementu **konfiguracji** elementu; w przeciwnym razie przejdź do następnego kroku.  
  
     **Środowiska uruchomieniowego** element nie ma żadnych atrybutów. **Konfiguracji** element może mieć tylko jeden **środowiska uruchomieniowego** element podrzędny.  
  
2.  W razie potrzeby dodaj **assemblybinding —** element jako element podrzędny elementu **środowiska uruchomieniowego** elementu; w przeciwnym razie przejdź do następnego kroku.  
  
     **Środowiska uruchomieniowego** element może mieć tylko jeden **assemblybinding —** elementu.  
  
3.  Dodaj następującą nazwę atrybutu, a do wartości **assemblybinding —** elementu:  
  
    |Nazwa atrybutu|Wartość atrybutu|  
    |--------------------|---------------------|  
    |**Xmlns**|**urn: schemas-microsoft-com:asm.v1**|  
  
4.  Dodaj **dependentAssembly** element jako element podrzędny elementu **assemblybinding —** elementu.  
  
     **DependentAssembly** element nie ma żadnych atrybutów.  
  
5.  Dodaj **assemblyIdentity** element jako element podrzędny **dependentAssembly** elementu.  
  
6.  Dodaj następujący atrybut nazwy i wartości do **assemblyIdentity** elementu:  
  
    |Nazwa atrybutu|Wartość atrybutu|  
    |--------------------|---------------------|  
    |**Nazwa**|**Microsoft.VisualStudio.Enterprise.ASPNetHelper**|  
    |**PublicKeyToken**|**b03f5f7f11d50a3a**|  
    |**Kultury**|**Neutralna**|  
  
7.  Dodaj **codeBase** element jako element podrzędny **dependentAssembly** elementu.  
  
8.  Dodaj następujący atrybut nazwy i wartości do **codeBase** elementu:  
  
    |Nazwa atrybutu|Wartość atrybutu|  
    |--------------------|---------------------|  
    |**Wersja**|**10.0.0.0**|  
    |**href**|`PathToASPNetHelperDll`|  
  
     `PathToASPNetHelperDll` jest Microsoft.VisualStudio.Enterprise.ASPNetHelper.dll adres URL pliku. Jeśli [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest zainstalowany w domyślnej lokalizacji **href** wartość powinna być `C:/Program%20Files/Microsoft%20Visual%20Studio%202010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL`  
  
```  
    <configuration>  
        <runtime>  
            <assemblyBinding   
                xmlns="urn:schemas-microsoft-com:asm.v1"  
            >  
                <dependentAssembly>  
                    <assemblyIdentity                         name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"   
                        publicKeyToken="b03f5f7f11d50a3a"                         culture="neutral"   
                    />  
                    <codeBase   
                        version="10.0.0.0"  
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"   
                    />  
                </dependentAssembly>  
            </assemblyBinding>  
        </runtime>  
```  
  
### <a name="to-add-the-profiler-post-process-step-to-the-configurationsystemwebcompilation-element"></a>Aby dodać do elementu configuration/system.web/compilation krok po przetwarzaniu profilera  
  
1.  W razie potrzeby dodaj **system.web** element jako element podrzędny elementu **konfiguracji** elementu; w przeciwnym razie przejdź do następnego kroku.  
  
     **System.web** element nie ma żadnych atrybutów. **Konfiguracji** element może mieć tylko jeden **system.web** element podrzędny.  
  
2.  W razie potrzeby dodaj **kompilacji** element jako element podrzędny elementu **system.web** elementu; w przeciwnym razie przejdź do następnego kroku.  
  
     **System.web** element może mieć tylko jeden **kompilacji** element podrzędny.  
  
3.  Usuń wszystkie istniejące atrybuty z **kompilacji** element i dodaj następujące nazwy atrybutu i wartości:  
  
    |Nazwa atrybutu|Wartość atrybutu|  
    |--------------------|---------------------|  
    |**assemblyPostProcessorType**|**Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter, Microsoft.VisualStudio.Enterprise.ASPNetHelper, wersja = 10.0.0.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a**|  
  
```  
    <configuration>  
        <runtime>  
        . . .  
        </runtime>  
        <system.web>  
            <compilation  
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,  
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,  
                    Version=10.0.0.0,  
                    Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"   
            />  
        </system.web>  
    <configuration>  
```  
  
### <a name="to-add-profiler-location-settings-to-the-configurationappsettings-element"></a>Aby dodać do elementu konfiguracji/appSettings ustawienia lokalizacji profilera  
  
1.  W razie potrzeby dodaj **appSettings** element jako element podrzędny elementu **konfiguracji** elementu; w przeciwnym razie przejdź do następnego kroku.  
  
     **AppSettings** element nie ma żadnych atrybutów. **Konfiguracji** element może mieć tylko jeden **appSettings** element podrzędny.  
  
2.  Dodaj **dodać** element jako element podrzędny **appSettings** elementu.  
  
3.  Dodaj następujący atrybut nazwy i wartości do **dodać** elementu:  
  
    |Nazwa atrybutu|Wartość atrybutu|  
    |--------------------|---------------------|  
    |**Klucz**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation**|  
    |**value**|`PerformanceToolsFolder` **\VSInstr.exe**|  
  
4.  Dodaj inny **dodać** element jako element podrzędny **appSettings** elementu.  
  
5.  Dodaj następujący atrybut nazwy i wartości do tego **dodać** elementu:  
  
    |Nazwa atrybutu|Wartość atrybutu|  
    |--------------------|---------------------|  
    |**Klucz**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools**|  
    |**value**|`PerformanceToolsFolder`|  
  
     `PerformanceToolsFolder` jest to ścieżka profilera plików wykonywalnych. Jeśli [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest zainstalowany w lokalizacji domyślnej, wartość będzie **10.0\Team C:\Program Files\Microsoft Visual Studio Tools narzędzia**  
  
```  
    <configuration>  
        <runtime>  
        . . .  
        </runtime>  
        . . .  
        <system.web>  
        </system.web>  
        <appSettings>  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\vsinstr.exe"  
        />  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\"  
            />  
        </appSettings>  
    </configuration>  
```  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się plik web.config pełną umożliwiający Instrumentację oraz profilowanie dynamicznie skompilowanej [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web. W tym przykładzie przyjęto założenie, że nie było żadnych innych ustawień w pliku przed modyfikacją.  
  
```  
<?xml version="1.0"?>  
    <configuration>  
        <runtime>  
            <assemblyBinding   
                xmlns="urn:schemas-microsoft-com:asm.v1"  
            >  
                <dependentAssembly>  
                    <assemblyIdentity   
                        name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"   
                        publicKeyToken="b03f5f7f11d50a3a"  
                        culture="neutral"   
                    />  
                    <codeBase   
                        version="10.0.0.0"  
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"   
                    />  
                </dependentAssembly>  
            </assemblyBinding>  
        </runtime>  
        <system.web>  
            <compilation  
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,  
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,  
                    Version=10.0.0.0,  
                    Culture=neutral,  
                    PublicKeyToken=b03f5f7f11d50a3a"   
            />  
        </system.web>  
        <appSettings>  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\vsinstr.exe"  
            />  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\"  
            />  
        </appSettings>  
    </configuration>  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Instrumentacja dynamicznie skompilowanej ASP.NET aplikacji i zbieranie szczegółowych danych o chronometrażu](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler.md)   
 [Porady: Instrumentacja dynamicznie skompilowanej ASP.NET aplikacji i zbieranie danych pamięci](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)