---
title: "AS2 Composants d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35113732-fe32-4776-be25-971ec66c365c
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1dbee64dc2e3484e85e6d8e41ce31a77713ffec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="as2-send-components"></a>Composants d'envoi AS2
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise plusieurs composants pour envoyer des messages AS2.  
  
## <a name="as2-send-pipelines"></a>Pipelines d'envoi AS2  
 La plus grande partie du traitement d'envoi AS2 est effectuée dans les pipelines d'envoi AS2 suivants. Ces pipelines sont installés dans `Microsoft.BizTalk.Edi.EdiIntPipelines.dll`, dans \Program Files\Microsoft BizTalk Server 20xx\Pipeline Components.  
  
> [!NOTE]
>  Le pipeline d'envoi AS2 est seulement pris en charge dans une instance d'hôte BizTalk 32 bits.  
  
 **AS2EDISend Pipeline**  
  
 Ce pipeline génère et envoie les messages EDI via AS2. Le pipeline est doté des composants suivants :  
  
-   Assembleur EDI  
  
-   Encodeur AS2  
  
 Ce pipeline n'est pas utilisé pour générer et envoyer des MDN via AS2, car l'assembleur EDI n'a pas besoin de traiter un MDN. Utilisez AS2SendPipeline pour envoyer des MDN.  
  
> [!NOTE]
>  L'exécution du pipeline AS2EDISend depuis une orchestration n'est pas prise en charge.  
  
 **Pipeline de AS2Send**  
  
 Ce pipeline envoie les messages via AS2 lorsque les messages ne sont pas codés dans EDI. Il envoie aussi les MDN via AS2. Le pipeline est doté des composants suivants :  
  
-   Encodeur AS2.  
  
 Si les messages à envoyer via AS2 ne sont pas de type EDI ou XML, vous pouvez créer un pipeline AS2Send personnalisé pour les gérer. Ce pipeline doit posséder un assembleur personnalisé pour convertir dans un autre format le XML intermédiaire dans BizTalk Server avant l'encodage du message dans EDIINT/AS2.  
  
> [!NOTE]
>  L'exécution du pipeline AS2Send depuis une orchestration n'est pas prise en charge.  
  
## <a name="as2-send-pipeline-components"></a>Composants de pipeline AS2Send  
 Les pipelines d'envoi AS2 utilisent les composants suivants. Ces composants sont installés dans `Microsoft.BizTalk.EdiInt.PipelineComponents.dll` dans \Program Files\Microsoft composants de BizTalk Server 20xx\Pipeline\\.  
  
 **Assembleur EDI**  
  
 Dans les pipelines d'envoi EDIINT, l'assembleur EDI sérialise l'échange EDI.  
  
 **Encodeur AS2**  
  
 L'encodeur AS2 est inclus à la phase d'encodage des pipelines d'envoi AS2. Il utilise le composant de pipeline S/MIME BizTalk pour fournir des fonctions d'encodage S/MIME aux messages AS2 et MDN. L'encodeur AS2 assure les tâches suivantes :  
  
-   Applique les en-têtes AS2/HTTP  
  
-   Signe les messages sortants, si activé  
  
-   Chiffre les messages sortants, si activé (pour EDI/AS2, pas MDN)  
  
-   Compresse le message, si activé (pour EDI/AS2, pas MDN)  
  
-   Stocke la charge utile au format câble si la **NRR activé pour les messages AS2 décodés sortants** propriété est sélectionnée et stocke le message au format câble si la **NRR activé pour les messages AS2 encodés sortants** propriété est sélectionnée.  
  
-   Calcule la valeur MIC et la stocke dans la banque de données.  
  
-   Met à jour et met des enregistrements en corrélation dans la base de données de réception de non-répudiation  
  
-   Pour les messages MDN, sert de pipeline Passthru, en routant le MDN généré par le décodeur AS2 dans le pipeline de réception AS2Receive. Si les paramètres de configuration le demandent, l'encodeur AS2 signe le MDN.  
  
    > [!NOTE]
    >  Le codage sur 8 bits est utilisé dans les messages AS2. Le codage Base64 n'est appliqué qu'aux signatures dans les messages AS2 et les  MDN.  
  
## <a name="http-adapter"></a>Adaptateur HTTP  
 Les ports d'envoi utilisés pour le traitement AS2 EDIINT utilisent l'adaptateur HTTP [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. L'adaptateur HTTP est configuré pour les transmissions unidirectionnelles et de type sollicitation-réponse.  
  
## <a name="non-repudiation-database"></a>Base de données de non-répudiation  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]utilise la base de données de non répudiation (la table EdiMessageContent de la base de données BizTalkDTADb) pour effectuer les opérations suivantes :  
  
> [!NOTE]
>  La table EdiMessageContent existe seulement dans la base de données BizTalkDTADb si l'une des propriétés d'accord de stockage de non-répudiation est vérifiée.  
  
-   Fournir un journal de non-répudiation pour le MDN signé  
  
-   Mettre en corrélation un message sortant à son MDN entrant  
  
-   Stocker des messages à différents changements d'état  
  
-   Associer les codes d'erreur à la réponse HTTP et à MDN  
  
-   Afficher les enregistrements selon des critères de filtre  
  
-   Archiver les enregistrements marqués  
  
> [!IMPORTANT]
>  Pour garantir l’authentification et l’intégrité des messages stockés dans la base de données de non-répudiation, les signatures numériques doivent être utilisés sur tous les messages qui sont stockés dans la base de données, les messages AS2 d’origine et MDN. Pour plus d’informations, consultez la section 9.1 de [RFC 1430, « Basé sur MIME sécurisé pair à pair de données commerciales échange via HTTP, Applicability Statement 2 (AS2) »](http://go.microsoft.com/fwlink/?LinkID=184212) ([http://go.microsoft.com/fwlink/?LinkID=184212](http://go.microsoft.com/fwlink/?LinkID=184212)).  
  
## <a name="see-also"></a>Voir aussi  
 [Envoi des Messages AS2 par BizTalk Server](../core/how-biztalk-server-sends-as2-messages.md)