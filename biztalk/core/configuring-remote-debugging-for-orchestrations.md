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
# <a name="configuring-remote-debugging-for-orchestrations"></a>Configuration du débogage à distance pour les orchestrations
Vous pouvez configurer complètement le débogage à distance entre le client et le serveur. La configuration du client est spécifiée dans Microsoft.XLANGs.BizTalk.Client.dll.config. La configuration du serveur est spécifiée dans le fichier BTSNTSvc.exe.config. Voici une liste de la configuration par défaut pour chacun.  
  
## <a name="client-microsoftxlangsbiztalkclientdllconfig"></a>Client (Microsoft.XLANGs.BizTalk.Client.dll.config)  
  
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
  
## <a name="serverbtsntsvcexeconfig"></a>Server(BTSNTSvc.exe.config)  
  
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
  
## <a name="configurable-parameters"></a>Paramètres configurables  
 La valeur par défaut garantit une configuration de sécurité maximale. Toutefois, l'utilisateur a la possibilité de modifier ces valeurs par défaut et les fichiers sont en format ACL puisqu'ils se trouvent dans le dossier des fichiers de programmes.  
  
 L’élément \<fournisseur / > est facultatif et si est omis, les canaux ne sont ne pas s’authentifient mutuellement à l’aide des récepteurs personnalisés. Il est toutefois dangereux de désactiver cette option car ceci a pour effet d'ouvrir les canaux. Cette procédure peut être réalisée dans le but d'améliorer les performances si aucune attaque de sécurité n'est à craindre.  
  
 L'élément channel peut avoir une propriété rejectRemoteRequests = true qui active uniquement les appels locaux et rejette les requêtes distantes.  
  
 L’attribut securityPackage dans le \<serverProviders / > élément peut avoir une des valeurs suivantes :  
  
-   negotiate  
  
-   ntlm  
  
-   Kerberos  
  
 L’attribut authenticationLevel le \<serverProviders / > élément peut avoir une des valeurs suivantes :  
  
-   packetPrivacy  - les messages seront chiffrés/déchiffrés  
  
-   packetIntegrity – les messages seront signés/vérifiés  
  
-   call  - les messages sont envoyés en l'état  
  
 L’attribut ref dans la \<channel / > élément peut être modifié en tcp ou http. Le port et le nom d’attribut dans le \<channel / > élément peut être également modifié sur des valeurs explicites.  
  
 Pour plus d'informations, consultez le Guide du développeur .NET Framework (propriétés de configuration de formateur et de canal).  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage des Orchestrations](../core/debugging-orchestrations.md)