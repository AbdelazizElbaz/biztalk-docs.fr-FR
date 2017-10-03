---
title: "AS2 Composants de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bdab87fd-15b9-4e3c-a4d7-984693262293
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c919a54a307a234237dd4086a0abf2a2c0c2fd8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="as2-receive-components"></a>Composants de réception AS2
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise plusieurs composants pour recevoir des messages AS2.  
  
## <a name="as2-receive-pipelines"></a>Pipelines de réception AS2  
 La plus grande partie du traitement de réception AS2 est effectuée dans les pipelines de réception AS2 suivants. Ces pipelines sont installés dans `Microsoft.BizTalk.EdiInt.PipelineComponents.dll` dans \Program Files\Microsoft composants de BizTalk Server 20xx\Pipeline\\.  
  
 **Pipeline de AS2EdiReceive**  
  
 Ce pipeline traite les messages EDI reçus via AS2, y compris les MDN. Le pipeline est doté des composants suivants :  
  
-   Décodeur AS2  
  
-   Désassembleur EDI  
  
-   BatchMarker.  
  
    > [!NOTE]
    >  Lors de l'utilisation du pipeline AS2EdiReceive, vous devez ajouter le compte d'utilisateur que le processus d'instance de l'hôte BizTalk isolé exécute sous le groupe Utilisateurs d'applications BizTalk. Le pipeline AS2EdiReceive s'exécute dans le processus d'instance de l'hôte BizTalk isolé. Le pipeline AS2EdiReceive accède au magasin SSO, qui requiert que l'utilisateur figure dans le groupe Utilisateurs d'applications BizTalk.  
  
 **AS2Receive Pipeline**  
  
 Ce pipeline traite les messages reçus via AS2 lorsque les messages ne sont pas codés dans EDI. Ces messages sont traités comme messages binaires. Le pipeline traite également les MDN reçus via AS2. Le pipeline est doté des composants suivants :  
  
-   Décodeur AS2  
  
-   Désassembleur AS2.  
  
## <a name="as2-receive-pipeline-components"></a>Composants du pipeline de réception AS2  
 Les pipelines de réception AS2 utilisent les composants suivants. Ces composants sont installés dans `Microsoft.BizTalk.EdiInt.PipelineComponents.dll` dans \Program Files\Microsoft composants de BizTalk Server 20xx\Pipeline\\.  
  
> [!NOTE]
>  Le pipeline de réception AS2 est seulement pris en charge dans une instance d'hôte BizTalk 32 bits.  
  
 **Décodeur AS2**  
  
 Le décodeur AS2 est inclus dans l'étape Décoder des pipelines de réception AS2EDIReceivePipeline et AS2Receive. Il utilise le composant de pipeline S/MIME BizTalk pour apporter des fonctions de décodage S/MIME aux messages AS2 et MDN.  
  
-   Traite les en-têtes AS2/HTTP  
  
-   Vérifie la signature, si le message a été signé  
  
-   Déchiffre les messages, si le message a été chiffré (pour un message EDI/AS2, pas un MDN)  
  
-   Décompresse le message, s'il était compressé  
  
-   Rapproche un MDN reçu du message sortant original  
  
-   Met à jour et met des enregistrements en corrélation dans la base de données de non-répudiation.  
  
-   Ecrit des enregistrements pour les rapports d'état AS2  
  
    > [!NOTE]
    >  Si une erreur survient au cours du traitement d'un message AS2 côté réception, le décodeur AS2 arrêtera le traitement des messages en aval (par exemple, le Désassembleur EDI n'analysera pas l'échange). Toutefois, le Désassembleur AS2 ou EDI doit toutefois générer le MDN.  
  
    > [!NOTE]
    >  Le codage sur 8 bits est utilisé dans les messages AS2. Le codage Base64 n'est appliqué qu'aux signatures dans les messages AS2 et les  MDN.  
  
 **Désassembleur AS2**  
  
 Dans le pipeline de réception AS2Receive, le Désassembleur AS2 effectue les opérations suivantes :  
  
-   Détermine si un MDN est requis et si le MDN doit être synchrone ou asynchrone.  
  
-   Génère un MDN AS2.  
  
-   Si le MDN est synchrone, il définit la propriété `EdiIntAS.IsAS2AsynchronousMDN` sur la valeur False ; s'il est asynchrone, il définit cette propriété sur la valeur True.  
  
-   Définit les jetons et les propriétés de corrélation sur le MDN.  
  
 **Désassembleur EDI**  
  
 Dans le AS2EDIReceivePipeline, le Désassembleur EDI analysera le message EDI dans un message XML intermédiaire en vue du traitement. Pour plus d’informations, consultez [EDI désassembleur fonctionnement](../core/how-the-edi-disassembler-works.md).  
  
 **BatchMarker**  
  
 Dans le AS2EDIReceivePipeline, le composant de pipeline BatchMarker définit les propriétés de contexte AgreementPartIdForSend et ToBeBatched nécessaires au traitement d'un échange par lot. Ce composant est inclus dans la dernière étape (résolution de l'accord) du pipeline AS2EDIReceive. Tous les pipelines chargés du traitement par lot des messages EDI doivent inclure le composant de pipeline BatchMarker.  
  
> [!NOTE]
>  Le composant de pipeline BatchMarker n'est pas inclus dans le pipeline AS2Receive utilisé pour le traitement des messages non-EDI. Toutefois, vous pouvez inclure le composant BatchMarker dans un pipeline de réception personnalisé qui ne contient pas le Désassembleur EDI. Pour plus d’informations, consultez « Traitement de Non-EDI Messages dans le composant de BatchMarker » dans [assembler un échange EDI par lot](../core/assembling-a-batched-edi-interchange.md).  
  
## <a name="http-adapter"></a>Adaptateur HTTP  
 Les ports et emplacements de réception utilisés pour le traitement AS2 utilisent l'adaptateur HTTP [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. L'adaptateur HTTP est configuré pour les transmissions unidirectionnelles et de type requête-réponse.  
  
## <a name="non-repudiation-database"></a>Base de données de non-répudiation  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]utilise la base de données de non répudiation (la table EdiMessageContent de la base de données BizTalkDTADb) pour effectuer les opérations suivantes :  
  
> [!NOTE]
>  La table EdiMessageContent existe seulement dans la base de données BizTalkDTADb si l'une des propriétés d'accord de stockage de non-répudiation a été sélectionnée.  
  
-   Fournit un journal de non-répudiation pour le MDN signé  
  
-   Associe un message sortant à son MDN entrant  
  
-   Stocke des messages à différents changements d'état  
  
-   Associe les codes d'erreur à la réponse HTTP et à MDN  
  
-   Affiche les enregistrements selon des critères de filtre  
  
-   Archive les enregistrements marqués.  
  
> [!IMPORTANT]
>  Pour garantir l'authentification et l'intégrité des messages stockés dans la base de données de réception de non-répudiation, les signatures numériques doivent être utilisées sur tous les messages devant être stockés dans la base de données, à la fois les messages AS2 et les MDN d'origine. Pour plus d’informations, consultez la section 9.1 de [RFC 1430, « Basé sur MIME sécurisé pair à pair de données commerciales échange via HTTP, Applicability Statement 2 (AS2) »](http://go.microsoft.com/fwlink/?LinkID=184212) ([http://go.microsoft.com/fwlink/?LinkID=184212](http://go.microsoft.com/fwlink/?LinkID=184212)).  
  
## <a name="see-also"></a>Voir aussi  
 [Réception des Messages AS2 par BizTalk Server](../core/how-biztalk-server-receives-as2-messages.md)