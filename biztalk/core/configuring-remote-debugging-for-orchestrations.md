---
title: "La configuration du débogage à distance pour les Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Microsoft.XLANGs.BizTalk.Client.dll.config, code sample
- BTSNTSvc.exe.config, code sample
- orchestrations, debugging
- building, debugging
- building, code sample
ms.assetid: 722efaec-d160-48dc-b94b-0733c9904d98
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4184b82efccd0ab2dcc2b871b6389b28148754c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-remote-debugging-for-orchestrations"></a><span data-ttu-id="57916-102">Configuration du débogage à distance pour les orchestrations</span><span class="sxs-lookup"><span data-stu-id="57916-102">Configuring Remote Debugging for Orchestrations</span></span>
<span data-ttu-id="57916-103">Vous pouvez configurer complètement le débogage à distance entre le client et le serveur.</span><span class="sxs-lookup"><span data-stu-id="57916-103">You can completely configure remote debugging between client and server.</span></span> <span data-ttu-id="57916-104">La configuration du client est spécifiée dans Microsoft.XLANGs.BizTalk.Client.dll.config. La configuration du serveur est spécifiée dans le fichier BTSNTSvc.exe.config. Voici une liste de la configuration par défaut pour chacun.</span><span class="sxs-lookup"><span data-stu-id="57916-104">The client configuration is specified in Microsoft.XLANGs.BizTalk.Client.dll.config. The server configuration is specified in BTSNTSvc.exe.config. The following is a listing of the default configuration for each.</span></span>  
  
## <a name="client-microsoftxlangsbiztalkclientdllconfig"></a><span data-ttu-id="57916-105">Client (Microsoft.XLANGs.BizTalk.Client.dll.config)</span><span class="sxs-lookup"><span data-stu-id="57916-105">Client (Microsoft.XLANGs.BizTalk.Client.dll.config)</span></span>  
  
```  
<configuration>  
     <system.runtime.remoting>  
  
 <channelSinkProviders>  
       <clientProviders>  
         <provider id="sspi" type="Microsoft.BizTalk.XLANGs.Client.SecurityClientChannelSinkProvider,Microsoft.XLANGs.BizTalk.Client" securityPackage="negotiate" authenticationLevel="packetPrivacy"/>  
       </clientProviders>  
</channelSinkProviders>  
  
<application>  
<channels>  
    <channel ref="tcp" port="0" name="">  
       <clientProviders>  
             <formatter ref="binary"/>  
             <provider ref="sspi" />  
        </clientProviders>  
       <serverProviders>  
             <formatter ref="binary" typeFilterLevel="Full"/>  
       </serverProviders>  
    </channel>  
</channels>  
</application>  
  </system.runtime.remoting>  
</configuration>  
```  
  
## <a name="serverbtsntsvcexeconfig"></a><span data-ttu-id="57916-106">Server(BTSNTSvc.exe.config)</span><span class="sxs-lookup"><span data-stu-id="57916-106">Server(BTSNTSvc.exe.config)</span></span>  
  
```  
<?xml version="1.0" ?>  
<configuration>  
    <runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
            <probing privatePath="BizTalk Assemblies;Developer Tools;Tracking;Tracking\interop" />  
        </assemblyBinding>  
    </runtime>  
  
    <system.runtime.remoting>  
  
        <channelSinkProviders>  
            <serverProviders>  
                <provider id="sspi" type="Microsoft.BizTalk.XLANGs.BTXEngine.SecurityServerChannelSinkProvider,Microsoft.XLANGs.BizTalk.Engine" securityPackage="ntlm" authenticationLevel="packetPrivacy" />  
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
  
## <a name="configurable-parameters"></a><span data-ttu-id="57916-107">Paramètres configurables</span><span class="sxs-lookup"><span data-stu-id="57916-107">Configurable Parameters</span></span>  
 <span data-ttu-id="57916-108">La valeur par défaut garantit une configuration de sécurité maximale.</span><span class="sxs-lookup"><span data-stu-id="57916-108">The default ensures maximum security configuration.</span></span> <span data-ttu-id="57916-109">Toutefois, l'utilisateur a la possibilité de modifier ces valeurs par défaut et les fichiers sont en format ACL puisqu'ils se trouvent dans le dossier des fichiers de programmes.</span><span class="sxs-lookup"><span data-stu-id="57916-109">However it is left to the user to change these defaults and these files are ACL'ed since they are in the program files folder.</span></span>  
  
 <span data-ttu-id="57916-110">L’élément \<fournisseur / > est facultatif et si est omis, les canaux ne sont ne pas s’authentifient mutuellement à l’aide des récepteurs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="57916-110">The element \<provider/> is optional and if not provided will cause the channels not to be mutually authenticated using the custom sinks.</span></span> <span data-ttu-id="57916-111">Il est toutefois dangereux de désactiver cette option car ceci a pour effet d'ouvrir les canaux.</span><span class="sxs-lookup"><span data-stu-id="57916-111">However this is a dangerous option to turn off as it will open up the channels.</span></span> <span data-ttu-id="57916-112">Cette procédure peut être réalisée dans le but d'améliorer les performances si aucune attaque de sécurité n'est à craindre.</span><span class="sxs-lookup"><span data-stu-id="57916-112">This can be done for better performance and when security attacks are not a concern.</span></span>  
  
 <span data-ttu-id="57916-113">L'élément channel peut avoir une propriété rejectRemoteRequests = true qui active uniquement les appels locaux et rejette les requêtes distantes.</span><span class="sxs-lookup"><span data-stu-id="57916-113">The channel element can have property rejectRemoteRequests = true which will enable only local calls and reject remote requests.</span></span>  
  
 <span data-ttu-id="57916-114">L’attribut securityPackage dans le \<serverProviders / > élément peut avoir une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="57916-114">The securityPackage attribute in the \<serverProviders/> element can have any of the following values:</span></span>  
  
-   <span data-ttu-id="57916-115">negotiate</span><span class="sxs-lookup"><span data-stu-id="57916-115">negotiate</span></span>  
  
-   <span data-ttu-id="57916-116">ntlm</span><span class="sxs-lookup"><span data-stu-id="57916-116">ntlm</span></span>  
  
-   <span data-ttu-id="57916-117">Kerberos</span><span class="sxs-lookup"><span data-stu-id="57916-117">Kerberos</span></span>  
  
 <span data-ttu-id="57916-118">L’attribut authenticationLevel le \<serverProviders / > élément peut avoir une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="57916-118">The authenticationLevel attribute in the \<serverProviders/> element can have any of the following values:</span></span>  
  
-   <span data-ttu-id="57916-119">packetPrivacy  - les messages seront chiffrés/déchiffrés</span><span class="sxs-lookup"><span data-stu-id="57916-119">packetPrivacy  - the messages will be encrypted/decrypted</span></span>  
  
-   <span data-ttu-id="57916-120">packetIntegrity – les messages seront signés/vérifiés</span><span class="sxs-lookup"><span data-stu-id="57916-120">packetIntegrity – the messages will be signed/verified</span></span>  
  
-   <span data-ttu-id="57916-121">call  - les messages sont envoyés en l'état</span><span class="sxs-lookup"><span data-stu-id="57916-121">call  - the messages will be sent as is</span></span>  
  
 <span data-ttu-id="57916-122">L’attribut ref dans la \<channel / > élément peut être modifié en tcp ou http.</span><span class="sxs-lookup"><span data-stu-id="57916-122">The ref attribute in the \<channel/> element can be changed to tcp or http.</span></span> <span data-ttu-id="57916-123">Le port et le nom d’attribut dans le \<channel / > élément peut être également modifié sur des valeurs explicites.</span><span class="sxs-lookup"><span data-stu-id="57916-123">The port and name attribute in the \<channel/> element can be changed as well to explicit values.</span></span>  
  
 <span data-ttu-id="57916-124">Pour plus d'informations, consultez le Guide du développeur .NET Framework (propriétés de configuration de formateur et de canal).</span><span class="sxs-lookup"><span data-stu-id="57916-124">For more information, see .NET Framework Developer's Guide (Channel and formatter configuration properties).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57916-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57916-125">See Also</span></span>  
 [<span data-ttu-id="57916-126">Débogage des Orchestrations</span><span class="sxs-lookup"><span data-stu-id="57916-126">Debugging Orchestrations</span></span>](../core/debugging-orchestrations.md)