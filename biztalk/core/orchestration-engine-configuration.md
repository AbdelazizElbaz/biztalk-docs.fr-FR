---
title: "Configuration du moteur d’orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestration engine, examples
- orchestration engine, code sample
- orchestration engine, dehydration
- orchestration engine, configuring
ms.assetid: d4f253c3-317d-4b52-bf54-81d50f03eeb3
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fbf64565534a368f7bfe084c6901cde62405fb62
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="orchestration-engine-configuration"></a><span data-ttu-id="ffd8b-102">Configuration du moteur d’orchestration</span><span class="sxs-lookup"><span data-stu-id="ffd8b-102">Orchestration Engine Configuration</span></span>
<span data-ttu-id="ffd8b-103">Le moteur d'orchestration se sert du fichier XML BTSNTSvc.exe.config pour déterminer certains comportements.</span><span class="sxs-lookup"><span data-stu-id="ffd8b-103">The orchestration engine uses an XML file called BTSNTSvc.exe.config to determine certain behaviors.</span></span> <span data-ttu-id="ffd8b-104">Par exemple, les propriétés de mise en attente et leurs valeurs par défaut sont configurées au format XML dans le fichier BTSNTSvc.exe.config et sont lues lorsque toutes les instances d'hôte contenant une orchestration sont démarrées.</span><span class="sxs-lookup"><span data-stu-id="ffd8b-104">For example, dehydration properties and their default values are configured as XML in the BTSNTSvc.exe.config file and are read when all host instances containing an orchestration start.</span></span> <span data-ttu-id="ffd8b-105">Pour plus d’informations, consultez [mise en attente de l’Orchestration et la réactivation](../core/orchestration-dehydration-and-rehydration.md).</span><span class="sxs-lookup"><span data-stu-id="ffd8b-105">For more information, see [Orchestration Dehydration and Rehydration](../core/orchestration-dehydration-and-rehydration.md).</span></span>  
  
 <span data-ttu-id="ffd8b-106">Un service lit ces informations de configuration une fois, au moment où il est démarré.</span><span class="sxs-lookup"><span data-stu-id="ffd8b-106">A service reads this configuration information once, when it is started.</span></span> <span data-ttu-id="ffd8b-107">Aucune modification apportée à ces informations n'est prise en compte, à moins d'arrêter le service, puis de le redémarrer.</span><span class="sxs-lookup"><span data-stu-id="ffd8b-107">Any changes to it will not be picked up unless the service is stopped and restarted.</span></span>  
  
 <span data-ttu-id="ffd8b-108">Vous trouverez ci-dessous des exemples pour des nœuds et des valeurs possibles.</span><span class="sxs-lookup"><span data-stu-id="ffd8b-108">See the examples below for different nodes and possible values.</span></span>  
  
## <a name="example-all-validations-on"></a><span data-ttu-id="ffd8b-109">Exemple : toutes les validations sur</span><span class="sxs-lookup"><span data-stu-id="ffd8b-109">Example: all validations on</span></span>  
  
```  
<?xml version="1.0" ?>  
<configuration>  
       <configSections>  
              <section   
                     name="xlangs"  
                     type="Microsoft.XLANGs.BizTalk.CrossProcess.XmlSerializationConfigurationSectionHandler, Microsoft.XLANGs.BizTalk.CrossProcess" />  
       </configSections>  
       <runtime>  
              <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
                     <probing privatePath="BizTalk Assemblies;Developer Tools;Tracking" />  
              </assemblyBinding>  
       </runtime>  
  
       <xlangs>  
              <Configuration>  
                     <Debugging   
                            ValidateAssemblies="true"  
                            ValidateSchemas="true"  
                            ValidateCorrelations="true"  
                            ExtendedLogging="true"  
                     />  
              </Configuration>  
       </xlangs>  
</configuration>  
```  
  
## <a name="example-assembly-validation-only"></a><span data-ttu-id="ffd8b-110">Exemple : validation assembly uniquement</span><span class="sxs-lookup"><span data-stu-id="ffd8b-110">Example: assembly validation only</span></span>  
  
```  
<?xml version="1.0" ?>  
<configuration>  
       <configSections>  
              <section   
                     name="xlangs"  
                     type="Microsoft.XLANGs.BizTalk.CrossProcess.XmlSerializationConfigurationSectionHandler, Microsoft.XLANGs.BizTalk.CrossProcess"  
              />  
       </configSections>  
       <runtime>  
              <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
                     <probing privatePath="BizTalk Assemblies;Developer Tools;Tracking" />  
              </assemblyBinding>  
       </runtime>  
  
       <xlangs>  
              <Configuration>  
                     <Debugging   
                            ValidateAssemblies="true"  
                            ExtendedLogging="false"  
                     />  
              </Configuration>  
       </xlangs>  
</configuration>  
```  
  
## <a name="example-remote-debugging-enabled"></a><span data-ttu-id="ffd8b-111">Exemple : le débogage distant activé</span><span class="sxs-lookup"><span data-stu-id="ffd8b-111">Example: remote debugging enabled</span></span>  
  
```  
<?xml version="1.0" ?>  
<configuration>  
       <runtime>  
              <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
                     <probing privatePath="BizTalk Assemblies;Developer Tools;Tracking" />  
              </assemblyBinding>  
       </runtime>  
  
       <system.runtime.remoting>  
              <customErrors mode="on"/>  
              <channelSinkProviders>  
                     <serverProviders>  
                            <provider id="sspi"  
                                    type="Microsoft.BizTalk.XLANGs.BTXEngine.SecurityServerChannelSinkProvider,Microsoft.XLANGs.BizTalk.Engine" securityPackage="negotiate" authenticationLevel="packetPrivacy" />  
                     </serverProviders>  
              </channelSinkProviders>  
  
              <application>  
                     <channels>  
                            <channel ref="tcp" port="0" name="">  
                                   <serverProviders>  
                                          <provider ref="sspi" />  
                                          <formatter ref="binary" typeFilterLevel="Full"/>  
                                   </serverProviders>  
                            </channel>  
                     </channels>  
              </application>  
       </system.runtime.remoting>  
</configuration>  
```  
  
## <a name="example-appdomain-configuration"></a><span data-ttu-id="ffd8b-112">Exemple : Configuration d’AppDomain</span><span class="sxs-lookup"><span data-stu-id="ffd8b-112">Example: AppDomain configuration</span></span>  
 <span data-ttu-id="ffd8b-113">Les assemblys sont assignés à des domaines nommés à l'aide de règles d'assignation (voir plus bas).</span><span class="sxs-lookup"><span data-stu-id="ffd8b-113">Assemblies are assigned to named domains using assignment rules (see more below).</span></span> <span data-ttu-id="ffd8b-114">Si aucune règle n'est spécifiée pour certains assemblys, ces derniers se voient assignés à un domaine ad hoc.</span><span class="sxs-lookup"><span data-stu-id="ffd8b-114">If no rule is specified for some assembly, the assembly will be assigned to an ad hoc domain.</span></span> <span data-ttu-id="ffd8b-115">Le nombre des assemblys ainsi assignés par domaine ad hoc est déterminé par la valeur du paramètre AssembliesPerDomain.</span><span class="sxs-lookup"><span data-stu-id="ffd8b-115">The number of such assigned assemblies per ad hoc domain is determined by the value of AssembliesPerDomain.</span></span>  
  
```  
<?xml version="1.0" ?>  
<configuration>  
    <configSections>  
        <section name="xlangs" type="Microsoft.XLANGs.BizTalk.CrossProcess.XmlSerializationConfigurationSectionHandler, Microsoft.XLANGs.BizTalk.CrossProcess" />  
    </configSections>  
    <runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
            <probing privatePath="BizTalk Assemblies;Developer Tools;Tracking" />  
        </assemblyBinding>  
    </runtime>  
    <xlangs>  
        <Configuration>  
            <!--   
                <!--   
AppDomain configuration.  
                Assemblies are assigned to named domains using assignment rules (see more below). If no rule is specified for some assembly, the assembly will be assigned to an ad hoc domain. The number of such assigned assemblies per ad hoc domain is determined by the value of AssembliesPerDomain.  
            -->-->   
            <AppDomains AssembliesPerDomain="10">  
                <!--   
                    <!--   
In this section the user may specify defualt configuration for any app domain created that does not have a named configuration associated with it (see AppDomainSpecs below)  
                    SecondsEmptyBeforeShutdown is the number of seconds that an app domain is empty (that is, it does not contain any orchestrations) before being unloaded. Specify -1 to signal that an app domain should never unload, even when empty.  
                    Similarly, SecondsIdleBeforeShutdown is the number of seconds that an app domain is idle (that is, it contains only dehydratable orchestrations) before being unloaded. Specify -1 to signal that an app domain should never unload when idle but not empty. When an idle but non-empty domain is shut down, all of the contained instances are dehydrated first.  
                -->  
                -->   
<DefaultSpec SecondsIdleBeforeShutdown="1200" SecondsEmptyBeforeShutdown="1800">  
                    <!--   
                        <!--   
BaseSetup is a serialized System.AppDomainSetup object. This is passed as-is to  
                        AppDomain.CreateAppDomain() and can be used to influence assembly search path etc.  
                    -->  
                    -->   
<BaseSetup>  
                        <ApplicationBase>c:\myAppBase</ApplicationBase>_0</ApplicationBase>   
                        <ConfigurationFile>c:\myAppBase\myConfig.config</ConfigurationFile>_0</ConfigurationFile>   
                    <DynamicBase>DynamicBase_0</DynamicBase>   
<DisallowPublisherPolicy>true</DisallowPublisherPolicy>   
<ApplicationName>ApplicationName_0</ApplicationName>   
<PrivateBinPath>PrivateBinPath_0</PrivateBinPath>   
<PrivateBinPathProbe>PrivateBinPathProbe_0</PrivateBinPathProbe>   
<ShadowCopyDirectories>ShadowCopyDirectories_0</ShadowCopyDirectories>   
<ShadowCopyFiles>ShadowCopyFiles_0</ShadowCopyFiles>   
<CachePath>CachePath_0</CachePath>   
<LicenseFile>LicenseFile_0</LicenseFile>   
<LoaderOptimization>NotSpecified</LoaderOptimization>   
</BaseSetup>  
                </DefaultSpec>  
                <!--   
                    - <!--   
In this section the user may specify named configurations for specific app domains, identified by their "friendly name". The format of any app-domain spec is identical to that of the default app-domain spec.  
                -->-->   
                <AppDomainSpecs>  
                    <AppDomainSpec Name="MyDomain1" SecondsIdleBeforeShutdown="-1" SecondsEmptyBeforeShutdown="12000">  
                        <BaseSetup>  
                            <PrivateBinPath>c:\PathForAppDomain1</PrivateBinPath>  
                        <PrivateBinPath>PrivateBinPath_0</PrivateBinPath>   
<PrivateBinPathProbe>PrivateBinPathProbe_0</PrivateBinPathProbe>   
</BaseSetup>  
                    </AppDomainSpec>  
                    <AppDomainSpec Name="MyFrequentlyUnloadingDomainMyTrashyDomain" SecondsIdleBeforeShutdown="60" SecondsEmptyBeforeShutdown="60" />   
                </AppDomainSpecs>  
                <!--   
                    <!--   
The PatternAssignmentRules and ExactAssignmentRules control assignment of assemblies to app domains.  
                    When a message arrives, the name of its corresponding orchestration's assembly is determined. Then, the assembly is assigned an app domain name. The rules guide this assignment. Exact rules are consulted first, in their order of definition, and then the pattern rules. The first match is used.  
                    If no match is found, the assembly will be assigned to an ad-hoc domain. The configuration and number of assemblies per ad-hoc domain is controlled by the AssembliesPerDomain attribute and the DefaultSpec section.  
                -->  
               -->   
- <ExactAssignmentRules>  
                    <!--   
                        <!--   
An exact assembly rule specifies a strong assembly name and an app domain name. If the strong assembly name equals the rule's assembly name, it is assigned to the corresponding app domain.  
                    -->-->   
                    <ExactAssignmentRule AssemblyName="BTSAssembly1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=9c7731c5584592ad"  
                       AssemblyName_0" AppDomainName="MyDomain1" />AppDomainName_1" />   
                    <ExactAssignmentRule AssemblyName="BTSAssembly2, Version=1.0.0.0, Culture=neutral, PublicKeyToken=9c7731c5584592ad"AssemblyName_0" AppDomainName="AppDomainName_1" />   
                        AppDomainName="MyFrequentlyUnloadingDomain " />  
                <ExactAssignmentRule AssemblyName="AssemblyName_0" AppDomainName="AppDomainName_1" />   
</ExactAssignmentRules>  
                <PatternAssignmentRules>  
                    <!--   
                        <!--   
A pattern assignment rule specifies a regular expression and an app domain name. If the strong assembly name matches the expression, it is assigned to the corresponding app domain. This allows version independent assignment, assignment by public key token, or assignment by the custom assembly key.  
                    -->-->   
                    <!--  
                        assign all assemblies with name BTSAssembly3, regardless of version and public key,  
                        to the MyDomain1 app domain   
                    -->  
                    <PatternAssignmentRule AssemblyNamePattern=" BTSAssembly3, Version=\d.\d.\d.\d, Culture=neutral, PublicKeyToken=.{16}"AssemblyNamePattern_0" AppDomainName=" MyDomain1" />  
                <PatternAssignmentRule AssemblyNamePattern="AssemblyNamePattern_0" AppDomainName="AppDomainName_1" />   
<PatternAssignmentRule AssemblyNamePattern="AssemblyNamePattern_0" AppDomainName="AppDomainName_1" />   
</PatternAssignmentRules>  
            </AppDomains>  
        </Configuration>  
    </xlangs>  
</configuration>  
```  
  
## <a name="modifying-other-sections-of-the-btsntsvcexeconfig-file"></a><span data-ttu-id="ffd8b-116">Modification d'autres sections du fichier BTSNTSvc.exe.config</span><span class="sxs-lookup"><span data-stu-id="ffd8b-116">Modifying other sections of the BTSNTSvc.exe.config file</span></span>  
 <span data-ttu-id="ffd8b-117">Pour plus d’informations sur la modification des valeurs de mise en attente dans le fichier BTSNTSvc.exe.config, consultez [propriétés par défaut de mise en attente](../core/dehydration-default-properties.md).</span><span class="sxs-lookup"><span data-stu-id="ffd8b-117">For information about modifying the dehydration values in BTSNTSvc.exe.config, see [Dehydration Default Properties](../core/dehydration-default-properties.md).</span></span>  
  
 <span data-ttu-id="ffd8b-118">Le fichier de configuration BTSNTSvc.exe contient plusieurs autres sections décrites dans les références générales de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ffd8b-118">The BTSNTSvc.exe configuration file contains several other sections documented in the .NET Framework General Reference.</span></span> <span data-ttu-id="ffd8b-119">Pour plus d’informations sur la modification de ces sections, consultez le **schéma de fichier de Configuration** de la référence générale du .NET Framework à [http://go.microsoft.com/FWLink/?LinkID=52964](http://go.microsoft.com/FWLink/?LinkID=52964).</span><span class="sxs-lookup"><span data-stu-id="ffd8b-119">For more information about the modification of these sections see the **Configuration File Schema** of the .NET Framework General Reference at [http://go.microsoft.com/FWLink/?LinkID=52964](http://go.microsoft.com/FWLink/?LinkID=52964).</span></span>  
  
 <span data-ttu-id="ffd8b-120">Outre les informations de configuration spécifiques à BizTalk, le fichier BTSNTSvc.exe.config est également où les composants d’application .NET qui s’exécutent dans le contexte d’une orchestration, un adaptateur ou un pipeline obtiennent leurs informations de configuration au moment de l’exécution à l’aide du .NET standard  **\<appSettings >** balise sous le  **\<configuration >** balise.</span><span class="sxs-lookup"><span data-stu-id="ffd8b-120">In addition to BizTalk-specific configuration information, the BTSNTSvc.exe.config file is also where .NET application components which run in the context of an orchestration, adapter or pipeline obtain their configuration information at run time using the standard .NET **\<appSettings>** tag under the **\<configuration>** tag.</span></span> <span data-ttu-id="ffd8b-121">Étant donné que BizTalk fournit déjà un mécanisme pour les adaptateurs personnalisés et les composants de pipeline obtenir des informations de configuration, le  **\<appSettings >** balise dans le fichier BTSNTSvc.exe.config doit généralement être utilisé par les composants .NET personnalisés appelé à partir d’une orchestration.</span><span class="sxs-lookup"><span data-stu-id="ffd8b-121">Because BizTalk already provides a mechanism for custom adapters and pipeline components to obtain configuration information, the **\<appSettings>** tag in the BTSNTSvc.exe.config file would typically be used by custom .NET components called from within an orchestration.</span></span> <span data-ttu-id="ffd8b-122">Exemple :</span><span class="sxs-lookup"><span data-stu-id="ffd8b-122">For example:</span></span>  
  
```  
<appSettings>  
     <add key="configParamName" value="configParamValue" />  
</appSettings>  
```  
  
## <a name="throttling-messages-per-orchestration"></a><span data-ttu-id="ffd8b-123">Limitation des messages par orchestration</span><span class="sxs-lookup"><span data-stu-id="ffd8b-123">Throttling Messages Per Orchestration</span></span>  
 <span data-ttu-id="ffd8b-124">Cette propriété, spécifiée dans le fichier btsntsvc.exe.config, empêche une orchestration d'utiliser trop de mémoire en limitant le nombre de messages en attente qu'elle peut avoir.</span><span class="sxs-lookup"><span data-stu-id="ffd8b-124">This property, specified in the btsntsvc.exe.config file, will prevent an orchestration from consuming too much memory by limiting the number of outstanding messages it can have.</span></span> <span data-ttu-id="ffd8b-125">Tous les messages continuent à être remis à la MessageBox ; Toutefois, les messages en file d’attente ne seront pas remis à l’orchestration jusqu'à ce qu’il traite certains de ses messages en attente.</span><span class="sxs-lookup"><span data-stu-id="ffd8b-125">All messages will continue to be delivered to the MessageBox; however, queued messages will not be delivered to the orchestration until it processes some of its outstanding messages.</span></span>  
  
 <span data-ttu-id="ffd8b-126">Pour spécifier cette propriété dans le fichier btsntsvc.exe.config (situé dans le répertoire racine de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]), ajoutez le paramètre suivant sous le nœud Application :</span><span class="sxs-lookup"><span data-stu-id="ffd8b-126">To specify this property in the btsntsvc.exe.config file (located in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] root directory), add the following parameter under Application node:</span></span>  
  
```  
<configuration>  
            <application>  
                        <Throttling PauseAt="100" ResumeAt="50" />  
            </application>  
</configuration>  
```  
  
 <span data-ttu-id="ffd8b-127">Dans cet exemple, une fois qu'une orchestration possède 100 messages en attente, la base de données MessageBox arrête l'envoi des messages.</span><span class="sxs-lookup"><span data-stu-id="ffd8b-127">In this example, once an orchestration has 100 outstanding messages, the MessageBox will stop sending additional messages.</span></span> <span data-ttu-id="ffd8b-128">Lorsque le nombre de messages en attente est 50, il indiquera que la MessageBox peut reprendre l’envoi des messages.</span><span class="sxs-lookup"><span data-stu-id="ffd8b-128">When the orchestration's number of outstanding messages is down to 50, it will specify the MessageBox can resume sending messages.</span></span> <span data-ttu-id="ffd8b-129">Vous pouvez spécifier d'autres valeurs.</span><span class="sxs-lookup"><span data-stu-id="ffd8b-129">You can specify other values.</span></span>  
  
 <span data-ttu-id="ffd8b-130">Vous devez également activer cette fonctionnalité, par hôte, dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="ffd8b-130">You must also enable this feature, per-host, in the database.</span></span> <span data-ttu-id="ffd8b-131">Pour activer la limitation des messages pour un hôte, modifiez la table dbo.Applications dans la base de données BizTalkMsgBoxDb.</span><span class="sxs-lookup"><span data-stu-id="ffd8b-131">To enable message throttling for a host, you must edit the dbo.Applications table in the BizTalkMsgBoxDb database.</span></span> <span data-ttu-id="ffd8b-132">Pour chaque hôte que vous souhaitez activer la limitation des messages par orchestration, définissez l’indicateur fAttributes sur 1.</span><span class="sxs-lookup"><span data-stu-id="ffd8b-132">For each host you want to enable message throttling per orchestration, set the fAttributes flag bit to 1.</span></span> <span data-ttu-id="ffd8b-133">Seuls les hôtes avec l’est défini sur 1 permettra de limitation des messages par orchestration.</span><span class="sxs-lookup"><span data-stu-id="ffd8b-133">Only those hosts with the fAttribute set to 1 will allow message throttling per orchestration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffd8b-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ffd8b-134">See Also</span></span>  
 <span data-ttu-id="ffd8b-135">[Débogage des Orchestrations](../core/debugging-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="ffd8b-135">[Debugging Orchestrations](../core/debugging-orchestrations.md) </span></span>  
 [<span data-ttu-id="ffd8b-136">Langage XLANG-s</span><span class="sxs-lookup"><span data-stu-id="ffd8b-136">XLANG-s Language</span></span>](../core/xlang-s-language.md)