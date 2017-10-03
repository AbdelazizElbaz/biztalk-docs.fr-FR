---
title: "Configuration de l’envoi et la réception des accusés de réception EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3db1c9f7-bafa-4659-a3c4-0faa56606081
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a88b7596772e951a835ffc13874ade7fefab5137
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-the-sending-and-receiving-of-edi-acknowledgments"></a>Configuration de l'envoi et de la réception des accusés de réception EDI
Pour configurer l'envoi d'un accusé de réception EDI en réponse à un échange reçu, vous devez procéder comme suit :  
  
-   Activez l'accusé de réception dans l'accord auquel correspond l'échange reçu. Ainsi, vous déclarez que le tiers qui a envoyé l'échange attend un accusé de réception.  
  
-   Si l'accusé de réception doit être renvoyé avec des propriétés spécifiques, telles que le terminateur CR LF activé, des caractères de séparation différents, etc., définissez ces propriétés dans l'autre onglet de l'accord unidirectionnel. Ainsi, vous configurez la manière dont le tiers renvoie l'accusé de réception.  
  
    > [!NOTE]
    >  Si un échange correspond à un accord défini dans le **pourquoi -> Tiersb** onglet, les propriétés relatives à la façon de générer l’accusé de réception sont configurées dans le **Tiersb -> Pourquoi** onglet. Cela est nécessaire car les propriétés de contexte d’accusé de réception pour l’expéditeur et récepteur les qualificateurs sont définis sur le contraire des valeurs que vous avez spécifié dans le **pourquoi -> Tiersb** onglet. Par exemple, si les identificateurs de l'expéditeur et du récepteur sont définis sur THEM et US dans l'accord auquel correspond le message d'échange, les propriétés de contexte de l'expéditeur et du récepteur sont définies sur US et THEM dans l'accusé de réception. De manière générale, l'autre onglet de l'accord unidirectionnel dispose également des identificateurs de l'expéditeur et du récepteur définis sur US et THEM, respectivement. Ainsi, le message d'accusé de réception correspond à cet accord et la configuration des propriétés est choisie. Par conséquent, si vous souhaitez disposer de l’accusé de réception à utiliser d’autres séparateurs d’éléments ou si vous souhaitez disposer de l’accusé de réception à utiliser CR LF, spécifiez les propriétés de la **Tiersb -> Pourquoi** onglet.  
  
     Sur le plan conceptuel, les propriétés de l'accusé de réception sont récupérées à partir de l'un des onglets de l'accord unidirectionnel possédant les mêmes qualificateurs d'expéditeur et de récepteur que ceux définis dans les propriétés de contexte de l'accusé de réception. Toutefois, pour des raisons de commodité, vous définissez ces propriétés sous l'autre onglet de l'accord unidirectionnel créé, auquel correspond l'échange.  
  
-   Si vous êtes un tiers qui renvoie un accusé de réception EDI au tiers qui a envoyé l'échange d'origine, configurez un port d'envoi unidirectionnel pour récupérer l'accusé de réception et l'envoyer ou un port de réception bidirectionnel pour envoyer l'accusé de réception. Pour plus d’informations, consultez [configuration d’un Port d’envoi statique pour envoyer les échanges EDI et les accusés de réception](../core/configuring-a-static-send-port-to-send-edi-interchanges-and-acknowledgments.md).  
  
-   Si vous êtes un tiers qui attend un accusé de réception EDI, configurez un port d'envoi bidirectionnel ou un port de réception unidirectionnel pour recevoir l'accusé de réception. Pour plus d’informations, consultez [configuration d’un Port de réception des Messages EDI et les accusés de réception](../core/configuring-a-port-to-receive-edi-messages-and-acknowledgments.md).  
  
-   L'application BizTalk EDI contient les schémas de contrôle. L'application contenant votre solution EDI doit donc comporter une référence à l'application BizTalk EDI. Pour plus d’informations, consultez [comment ajouter une référence à l’Application EDI de BizTalk Server](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-request-an-acknowledgment-for-the-party-that-sent-the-original-interchange"></a>Pour demander un accusé de réception pour le tiers qui a envoyé l'échange d'origine  
  
1.  > [!NOTE]
    >  En exécutant les étapes de cette procédure, vous configurez que le tiers qui envoie l'échange attend un accusé de réception en retour.  
  
     Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur le **Parties** nœud. Dans le **tiers et profils d’entreprise** , cliquez sur le tiers qui a l’accord pour lequel vous devez activer l’accusé de réception. Dans le **accord** section de la page, cliquez sur l’accord, sur **propriétés**. Dans le **propriétés de l’accord** boîte de dialogue, sous l’onglet d’accord unidirectionnel (auquel l’échange entrant résoudra), procédez comme suit :  
  
    1.  Dans le **identificateurs** , entrez les valeurs pour l’expéditeur et récepteur qualificateurs.  
  
         Pour un accusé de réception X12, entrez des valeurs pour ISA5, ISA6, ISA7 et ISA8. Pour ISA5 et ISA6, entrez les valeurs pour le tiers qui envoie l'échange. Pour ISA7 et ISA8, entrez les valeurs pour le tiers qui reçoit l'échange.  
  
         Pour un accusé de réception EDIFACT, entrez des valeurs pour UNB2.1, UNB2.2, UNB3.1 et UNB3.2. Pour UNB2.1 et UNB2.2, entrez les valeurs pour le tiers qui envoie l'échange. Pour UNB3.1 et UNB3.2, entrez les valeurs pour le tiers qui reçoit l'échange.  
  
    2.  Dans le **accusés de réception** page, sélectionnez les propriétés définissant le type d’accusé de réception que le tiers expéditeur attend :  
  
         Pour X12 accusés de réception, sélectionnez **TA1 attendu** et/ou **997 attendu** selon les accusés de réception attendus. Pour chaque type d’accusé de réception, sélectionnez **ne ne pas traiter par lot \<type d’accusé de réception >** si vous souhaitez que chaque instance d’un accusé de réception envoyés sous la forme d’un échange distinct.  
  
         Pour les accusés de réception EDIFACT, sélectionnez **réception du message (CONTRL) attendu** et/ou **accusé de réception (CONTRL) attendu** selon les accusés de réception attendus. Pour chaque type d’accusé de réception, sélectionnez **ne ne pas traiter par lot \<type d’accusé de réception >** si vous souhaitez que chaque instance d’un accusé de réception envoyés sous la forme d’un échange distinct.  
  
    3.  Dans le **paramètres d’hôte Local** page sous le **paramètres de l’échange** section, désactivez le **port de réception de l’accusé de réception itinéraire un pipeline d’envoi de requête-réponse** pour renvoyer le accusé de réception asynchrone via un port d’envoi unidirectionnel. Gardez cette propriété activée pour renvoyer l'accusé de réception de manière synchrone, sur un port de réception bidirectionnel.  
  
    4.  Dans le **Ports d’envoi** page, dans le **nom** colonne de la **ports d’envoi** grille, sélectionnez le port d’envoi que vous avez configuré pour envoyer l’accusé de réception.  
  
        > [!NOTE]
        >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise ce paramétrage de port d'envoi pour déterminer le tiers à utiliser lors du traitement du message. Pour plus d’informations, consultez [résolution de l’accord et détermination du schéma pour les Messages EDI sortants](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md).  
  
        > [!NOTE]
        >  Si vous n'avez pas configuré le port d'envoi, vous devrez peut-être effectuer cette opération ultérieurement.  
  
### <a name="to-configure-how-the-party-sends-the-acknowledgement-back"></a>Pour configurer la manière dont le tiers renvoie l'accusé de réception  
  
1.  > [!NOTE]
    >  En exécutant les étapes de cette procédure, vous configurez la manière dont le tiers qui a reçu l'échange renvoie un accusé de réception.  
  
     Dans le même **propriétés de l’accord** boîte de dialogue, dans l’autre onglet d’accord unidirectionnel, procédez comme suit :  
  
    1.  Dans le **identificateurs** , entrez les valeurs pour l’expéditeur et récepteur qualificateurs.  
  
        > [!NOTE]
        >  Lors de l'envoi de l'accusé de réception, le tiers qui a reçu l'échange d'origine devient l'expéditeur et le tiers qui a envoyé l'échange d'origine devient le récepteur. Par conséquent, les valeurs que vous entrez dans la page Identificateurs sont désormais les valeurs opposées à celles que vous avez spécifiées sous l'onglet de l'accord unidirectionnel, à l'étape précédente. Cela a deux objectifs :  
        >   
        >  -   Le renvoi de l'accusé de réception correspond à cet accord unidirectionnel que vous créez car les propriétés de contexte de l'expéditeur et du récepteur sur l'accusé de réception correspondent aux valeurs de l'expéditeur et du récepteur que vous entrez maintenant dans la page Identificateurs.  
        > -   Cet onglet de l'accord permet de configurer toute personnalisation à inclure dans l'accusé de réception. Par exemple, vous pouvez utiliser d'autres séparateurs ou activer le terminateur CR LF, etc.  
  
         Pour un accusé de réception X12, entrez des valeurs pour ISA5, ISA6, ISA7 et ISA8. Pour ISA5 et ISA6, entrez les valeurs pour le tiers qui envoie l'accusé de réception (les mêmes que pour le tiers qui a reçu l'échange d'origine). Pour ISA7 et ISA8, entrez les valeurs pour le tiers qui reçoit l'accusé de réception (les mêmes que pour le tiers qui a envoyé l'échange d'origine.)  
  
         Pour un accusé de réception EDIFACT, entrez des valeurs pour UNB2.1, UNB2.2, UNB3.1 et UNB3.2. Pour UNB2.1 et UNB2.2, entrez les valeurs pour le tiers qui envoie l'accusé de réception (les mêmes que pour le tiers qui a reçu l'échange d'origine). Pour UNB3.1 et UNB3.2, entrez les valeurs pour le tiers qui reçoit l'accusé de réception (les mêmes que pour le tiers qui a envoyé l'échange d'origine).  
  
    2.  Pour un X12 EDIFACT accusé de réception ou, si nécessaire, dans le **jeu de caractères et séparateurs** page, spécifiez les séparateurs que vous souhaitez utiliser dans l’accusé de réception. Vous pouvez également spécifier si l'accusé de réception doit utiliser un suffixe CR LF.  
  
    3.  Pour un accusé de réception EDIFACT, si nécessaire, dans le **enveloppes** page sous le **paramètres de l’échange** section, spécifiez si l’accusé de réception inclut un segment UNA ou un segment UNG en sélectionnant le options appropriées.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des accusés de réception EDI](../core/configuring-edi-acknowledgments.md)   
 [Service EDI et des schémas de contrôle](../core/edi-service-and-control-schemas.md)   
 [Envoi d’un accusé de réception EDI](../core/sending-an-edi-acknowledgment.md)   
 [Comment créer un Port de réception](../core/how-to-create-a-receive-port.md)   
 [Comment créer un Port d’envoi](../core/how-to-create-a-send-port2.md)