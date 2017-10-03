---
title: Comment utiliser les tableaux de Service Web | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP adapters, Web services
- Web services, arrays
- orchestrations, Web services
- orchestrations, Web ports
ms.assetid: 29ecaaed-aa8a-4cf9-a7c8-4b0d6dd412ac
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e78f12405c9c331a888a268d39e2a1520c84fdc8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-consume-web-service-arrays"></a>Utilisation des tableaux de service Web
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet d'utiliser les tableaux exposés dans les services Web à partir d'une orchestration BizTalk.  
  
 **Pour configurer une Orchestration pour utiliser un tableau exposé dans un service Web :**  
  
 Déterminez l'URL du service Web qui expose des tableaux. Il s'agit généralement d'une page Web asmx qui répertorie les opérations prises en charge par le service Web. Par exemple : http://localhost/ArrayWS/ArraySvc.asmx.  
  
1.  Ajoutez une référence Web à cette URL dans le projet Visual Studio qui contient votre orchestration :  
  
    -   Dans l’Explorateur de solutions, cliquez sur **références**, puis cliquez sur **ajouter une référence de Service**.  
  
    -   Dans le **ajouter une référence de Service** boîte de dialogue, cliquez sur **avancé**.  
  
    -   Dans le **paramètres de référence de Service** boîte de dialogue, cliquez sur **ajouter une référence Web** dans les **compatibilité** section.  
  
    -   Dans le **ajouter une référence Web** boîte de dialogue, entrez l’URL du service Web dans le **URL** zone de texte, puis cliquez sur **accédez**.  
  
    -   Entrez un nom pour la référence Web dans le **nom de référence Web** zone de texte et cliquez sur le **ajouter une référence** bouton.  
  
    -   La référence Web s’affiche sous **références Web** dans l’Explorateur de solutions.  
  
        > [!TIP]
        >  Une fois que vous avez ajouté au projet, une référence Web le **ajouter une référence Web** commande est directement disponible lorsque vous cliquez sur le nom du projet ou **références** ou **lesréférencesWeb**.  
  
2.  Ajouter un port Web à votre orchestration :  
  
    -   Faites glisser un **Port** met en évidence la forme à partir de la boîte à outils à un de port dans le Concepteur d’Orchestration pour lancer le **Assistant Configuration du Port**. Cliquez sur le **suivant** situé dans le **Assistant Configuration du Port** pour afficher les **propriétés de Port** boîte de dialogue.  
  
    -   Entrez une valeur dans la **nom** zone de texte pour identifier le port, puis cliquez sur le **suivant** bouton pour afficher la **sélectionner un Type de Port** boîte de dialogue.  
  
    -   Sélectionnez l’option de **utiliser un Type de Port existant**, sélectionnez le Port Web type qui correspond au site Web référence ajoutée, puis cliquez sur le **suivant** bouton pour afficher la **deliaisondePort**boîte de dialogue.  
  
    -   Dans le **liaison de Port** boîte de dialogue Sélectionnez la **liaison de Port** , puis cliquez sur le **suivant** , puis cliquez sur le **Terminer** bouton. Vous devez maintenant avoir un port Web affiché dans le Concepteur d’Orchestration qui inclut les opérations prises en charge par le service Web.  
  
3.  Ajouter **envoyer** et **réception** formes à votre Orchestration comme il convient :  
  
    -   Faites glisser un **envoyer** forme à partir de la boîte à outils vers une ligne de connexion dans l’aire du Concepteur d’Orchestration pour configurer l’orchestration pour envoyer un message de demande au port Web. Si vous vous connectez le **envoyer** forme une du port Web demandent des connecteurs de message, BizTalk crée automatiquement un message du type approprié à utiliser lors de l’envoi d’un message de demande à ce port.  
  
    -   Faites glisser un **réception** forme à partir de la boîte à outils vers une ligne de connexion dans l’aire du Concepteur d’Orchestration pour configurer l’orchestration pour recevoir un message de réponse du port Web. Si vous vous connectez le **réception** forme à un des connecteurs de message de réponse de port Web, BizTalk crée automatiquement un message du type approprié à utiliser lors de la réception d’un message de réponse à partir de ce port.  
  
> [!NOTE]
>  L'adaptateur SOAP permet d'envoyer des messages à un service Web ou d'en recevoir d'un service Web. Pour plus d’informations sur la configuration de l’adaptateur SOAP, consultez [configuration de l’adaptateur SOAP](../core/configuring-the-soap-adapter.md).  
  
 Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] moteur d’Orchestration fournit la prise en charge pour les deux une consommation de tableaux et en escalier exposés par les services Web. Si vous ajoutez une référence Web à un service Web qui expose des tableaux, le Concepteur d'orchestration génère un type de message Web qui décrit le tableau. Vous pouvez alors envoyer et recevoir des messages de ce type comme n'importe quel autre message. BizTalk Server ne limite pas l'envoi de messages Web contenant des tableaux aux seuls ports Web.  
  
 Pour obtenir un exemple d’utilisation des tableaux de service Web, consultez l’exemple du Kit de développement logiciel « Consume Web Services » et « Utilisation de Services Web with Array Parameters » à [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de Messages dans les Orchestrations](../core/using-messages-in-orchestrations.md)