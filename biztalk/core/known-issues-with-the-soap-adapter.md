---
title: "Problèmes connus avec l’adaptateur SOAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3229d73-170d-42b7-bab9-12ae5f2d0fa7
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 671510c6901fc399580ab73018e67eadc86f7212
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-the-soap-adapter"></a>Problèmes connus avec l'adaptateur SOAP
Cette section contient des informations qui peuvent vous permettre d'éviter certaines erreurs.  
  
## <a name="known-issues"></a>Problèmes connus  
  
#### <a name="the-soap-adapter-experiences-poor-performance-or-generates-errors-under-load"></a>L'adaptateur SOAP rencontre des problèmes de performances ou génère des erreurs en conditions de charge  
  
##### <a name="problem"></a>Problème  
 L'adaptateur SOAP rencontre des problèmes de performances ou génère des erreurs en conditions de charge  
  
##### <a name="cause"></a>Cause  
 Ce problème survient car les options de configuration par défaut de l'adaptateur SOAP ou des composants de dépendances qui ont un impact sur l'adaptateur SOAP ne sont pas configurés pour les performances en cas de charge.  
  
##### <a name="resolution"></a>Résolution  
 Pour résoudre ce problème, modifiez les options de configuration de l’adaptateur SOAP ou des composants de dépendance décrites dans la rubrique [les paramètres de Configuration qui affectent les performances carte](../core/configuration-parameters-that-affect-adapter-performance.md).  
  
#### <a name="the-mimesmime-encoder-and-decoder-pipeline-components-cannot-encode-and-decode-data-processed-by-the-soap-adapter"></a>Les composants de pipeline Encodeur et Décodeur MIME/SMIME ne peuvent ni coder ni décoder les données traitées par l'adaptateur SOAP  
  
##### <a name="problem"></a>Problème  
 Les composants de pipeline Encodeur et Décodeur MIME/SMIME ne peuvent ni coder ni décoder les données traitées par l'adaptateur SOAP  
  
##### <a name="cause"></a>Cause  
 Ce problème se produit car l'adaptateur SOAP assemble et désassemble les messages SOAP dans l'étape du processus le concernant.  
  
##### <a name="resolution"></a>Résolution  
 Pour résoudre ce problème, utilisez SSL (Secure Sockets Layer) pour sécuriser les communications de codage des messages traités par l'adaptateur SOAP. Sur le côté envoi, utilisez le **empreinte de certificat Client** propriété dans la page de propriétés de l’adaptateur SOAP pour effectuer cette opération. Au niveau de la réception, vous devez configurer le répertoire virtuel qui héberge le service Web BizTalk pour les communications SSL sécurisées.  
  
#### <a name="the-default-appdomain-hosting-the-soap-adapter-gets-unloaded-causing-the-host-process-to-hang"></a>Le domaine d'application AppDomain par défaut hébergeant l'adaptateur SOAP est déchargé, ce qui provoque le blocage du processus hôte  
  
##### <a name="problem"></a>Problème  
 Le processus hébergeant l'adaptateur SOAP se bloque, ce qui provoque le blocage de tous les autres services Web du processus. Cela peut donner lieu à l'erreur suivante :  
  
 Échec de l’exécution du pipeline de réponse : Source « Inconnu » : « inconnu » recevoir Port : "TwoWayLatencyLoopBack_RxPort » URI : « / /twowaylatencyrxsoap/twowaylatencyws.asmx » raison : tenté d’accéder à un AppDomain non chargé.  
  
##### <a name="cause"></a>Cause  
 L'adaptateur SOAP s'exécute dans l'espace de processus IIS. Si le pool d'applications AppPool de IIS contient plusieurs services Web, chacun d'entre eux dispose au final de son propre AppDomain.  
  
 Par défaut, tous les objets du moteur de messagerie sont créés dans le premier AppDomain (c'est-à-dire,. le domaine d’application correspondant au premier service Web). Si le premier service Web est inactif pendant une période prolongée, quelle qu'en soit la raison, IIS décharge le premier AppDomain. Dans ce cas, tous les services du processus d'hébergement deviennent inutilisables.  
  
##### <a name="resolution"></a>Résolution  
 Pour éviter le déchargement du domaine d’application AppDomain, procédez comme suit :  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk Server** puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans **Console d’Administration de BizTalk Server**, Expand **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis cliquez sur **hôtes**.  
  
3.  Dans la liste des ordinateurs hôtes, cliquez sur l’hôte requis, puis cliquez sur **paramètres**.  
  
4.  Dans le **Panneau de configuration BizTalk**, vérifiez **domaine d’application par défaut pour un adaptateur isolé** sous **général** onglet.  
  
 Ceci fait, les objets du moteur de messagerie BizTalk sont créés dans le domaine d'application AppDomain par défaut et non dans leur propre AppDomains. Le domaine d'application AppDomain par défaut n'étant jamais déchargé, ce problème ne se produit plus.  
  
#### <a name="the-soap-adapter-fails-to-register"></a>Échec de l'inscription de l'adaptateur SOAP  
  
##### <a name="problem"></a>Problème  
 L'erreur suivante peut se produire lorsque BizTalk Server tente d'inscrire l'adaptateur SOAP (ou HTTP).  
  
 « Le moteur de messagerie n'a pas pu inscrire l'adaptateur "SOAP". Détails : « inscription de différents types d’adaptateur dans le même processus n’est pas un scénario pris en charge. Ainsi, les adaptateurs de réception HTTP et SOAP ne peuvent pas coexister dans le même processus. »  
  
 Ou  
  
 « Le moteur de messagerie n'a pas pu inscrire l'adaptateur "HTTP". Détails : « inscription de différents types d’adaptateur dans le même processus n’est pas un scénario pris en charge.  Ainsi, les adaptateurs de réception HTTP et SOAP ne peuvent pas coexister dans le même processus. »  
  
##### <a name="cause"></a>Cause  
 Lors de l'exécution de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] / IIS 6.x, les adaptateurs SOAP et HTTP ne peuvent pas s'exécuter dans le même espace de processus ou pool d'applications.  
  
##### <a name="resolution"></a>Résolution  
 Si une installation requiert l'utilisation des adaptateurs SOAP et HTTP sur le même serveur Web, des pools d'applications distincts doivent être créés pour chaque adaptateur.  Une fois créés, les répertoires virtuels de chaque adaptateur sont chacun assignés à un pool d'applications différent.  
  
> [!NOTE]
>  Ce problème ne se produit pas sous Windows XP car, sous ce système d'exploitation, les adaptateurs SOAP et HTTP s'exécutent dans des espaces de processus différents sous IIS 5.x.  L'adaptateur SOAP s'exécute en tant qu'application ASP.Net dans le processus aspnet_wp.exe.  L'adaptateur HTTP s'exécute dans l'espace de processus dédié de dllhost.exe.  Les deux adaptateurs sont donc isolés l'un de l'autre, et peuvent donc s'exécuter sur le même serveur Web simultanément.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage de l’adaptateur SOAP](../core/troubleshooting-the-soap-adapter.md)