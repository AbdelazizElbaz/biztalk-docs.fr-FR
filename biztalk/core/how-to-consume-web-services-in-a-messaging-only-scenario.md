---
title: "L’utilisation de Web Services dans un scénario de messagerie seule | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66873959-5b1b-4d9b-ad19-f083670420b8
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ac3e87d54ab7babed8be6b4d81267d22d8ac319
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-consume-web-services-in-a-messaging-only-scenario"></a>Utilisation des services Web dans un scénario de messagerie seule
Une nouvelle amélioration apportée à l'adaptateur SOAP réside dans la capacité à appeler les services Web dans un scénario de messagerie seule à l'aide de ports d'envoi de routage basé sur le contenu. Cette fonctionnalité permet d'utiliser des services Web sans créer d'orchestrations. Elle offre également de meilleures performances dans l'utilisation des services Web, car les messages ne sont pas transmis via les orchestrations.  
  
 Pour utiliser des services Web dans un scénario de messagerie seule, procédez comme suit :  
  
-   Créez une bibliothèque proxy et des schémas XML pour l'appel de services Web.  
  
-   Configurez un port d'envoi et un emplacement de réception pour l'utilisation d'un service Web.  
  
### <a name="to-create-a-proxy-library-and-xml-schemas-for-invoking-web-services"></a>Pour créer une bibliothèque proxy et des schémas XML pour l'appel de services Web  
  
1.  Déterminez l'URL du service Web.  
  
2.  Ouvrir un **projet BizTalk Server vide** dans un [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] solution. Pour plus d’informations sur la création d’un projet BizTalk Server, consultez [comment créer des projets BizTalk](../core/how-to-create-biztalk-projects.md).  
  
    > [!NOTE]
    >  Cette procédure pas à pas utilise un projet BizTalk Server pour permettre de générer les bibliothèques proxy et les schémas XML utilisés par le service Web. Vous pouvez également utiliser le Wsdl.exe et Xsd.exe dans le Kit de développement logiciel .NET Framework 4.0 dans le même but.  
  
3.  Dans l’Explorateur de solutions, cliquez sur le nom de projet BizTalk Server, puis cliquez sur **ajouter une référence de Service**.  
  
4.  Dans le **ajouter une référence de Service** boîte de dialogue, cliquez sur **avancé**.  
  
5.  Dans le **paramètres de référence de Service** boîte de dialogue, cliquez sur **ajouter une référence Web** dans les **compatibilité** section.  
  
6.  Dans le **ajouter une référence Web** boîte de dialogue zone, procédez comme suit :  
  
    1.  Dans le **URL** champ, tapez l’URL du service Web, puis cliquez sur **accédez**.  
  
    2.  Dans le **nom de référence Web** champ, tapez un nom pour l’espace de noms, puis cliquez sur **ajouter une référence**.  
  
7.  La référence Web s’affiche sous **références Web** nœud dans l’Explorateur de solutions.  
  
    > [!TIP]
    >  Une fois que vous avez ajouté à un projet BizTalk, une référence web le **ajouter une référence Web** commande est directement disponible lorsque vous cliquez sur le nom du projet ou **références** ou **lesréférencesWeb**.  
  
8.  Dans l’Explorateur de solutions, cliquez sur le nom du projet, puis cliquez sur **propriétés** pour lancer le Concepteur de projet.  
  
9. Dans le Concepteur de projets, cliquez sur le **signature** onglet.  
  
10. Sélectionnez **signer l’assembly** , cliquez sur la liste déroulante pour le **choisir un fichier de clé de nom fort**, puis cliquez sur **Parcourir**.  
  
11. Recherchez et sélectionnez le fichier de clé d’assembly, puis cliquez sur **ouvrir**.  
  
12. Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Générer**.  
  
13. Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Déployer**.  
  
### <a name="to-configure-a-send-port-and-receive-location-for-consuming-a-web-service"></a>Pour configurer un port d'envoi et un emplacement de réception pour l'utilisation d'un service Web  
  
1.  Dans la console Administration de BizTalk Server, créez un port d'envoi. Pour plus d’informations, consultez [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md). Lors de la création d'un port d'envoi, sélectionnez le type de transport ou protocole de transport SOAP.  
  
2.  Configurez le port d'envoi SOAP avec les paramètres suivants. Pour plus d’informations, consultez [comment configurer un Port d’envoi SOAP](../core/how-to-configure-a-soap-send-port.md).  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Les paramètres suivants**|Sélectionner cette option pour spécifier les propriétés suivantes.|  
    |**Nom de l’assembly**|Sélectionner l'assembly créé dans la procédure précédente. Le nom qualifié complet de l’assembly est écrit à l’adaptateur SOAP **AssemblyName** propriété.|  
    |**Nom de type**|Indiquez le nom de la classe contenant la méthode Web à appeler. Le nom de type est écrit à l’adaptateur SOAP **TypeName** propriété.|  
    |**Nom de la méthode**|Spécifier une des méthodes dans la zone de liste. La méthode Web est écrit à l’adaptateur Soap **MethodName** propriété.|  
  
    > [!NOTE]
    >  Si vous souhaitez utiliser le routage basé sur le contenu, configurez le filtre du port d'envoi. Pour plus d’informations, consultez [comment configurer des filtres pour un Port d’envoi](../core/how-to-configure-filters-for-a-send-port.md).  
  
    > [!NOTE]
    >  S'il n'existe aucun abonné aux messages de réponse des services Web appelés, une erreur de défaillance du routage se produit.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de Services Web](../core/consuming-web-services.md)