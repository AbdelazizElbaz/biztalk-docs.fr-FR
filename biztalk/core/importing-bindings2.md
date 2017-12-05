---
title: "L’importation Bindings2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bindings, requirements
- importing, bindings
- bindings, importing
ms.assetid: 9e10bc04-aba8-430a-b8fd-de9399d54f88
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f2c92d5469f88494c77ad062d97c53768572a5b
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="importing-bindings"></a>Importation des liaisons
Les rubriques de cette section expliquent comment importer des liaisons dans une application ou un groupe BizTalk.  
  
 Lorsque vous importez des liaisons, gardez les points importants suivants à l'esprit :  
  
-   **Les liaisons existantes sont écrasées.** Si les liaisons que vous importez ont le même nom que les liaisons existantes, ces dernières seront remplacées. En outre, si le fichier de liaison contient des tiers et alias, les liaisons des tiers et alias ayant le même nom qui existent déjà dans l'application sont remplacées.  
  
-   **Toutes les liaisons dans un groupe doivent être uniques.** Si une liaison ayant le même nom que celle que vous importez existe déjà dans le groupe, l'opération d'importation échouera.  
  
-   **Vous devez reconfigurer les mots de passe.** Pour des raisons de sécurité, lorsque vous exportez un fichier de liaison, BizTalk Server ne conserve pas les mots de passe des liaisons du fichier. Une fois les liaisons importées, vous devez reconfigurer les mots de passe des ports d'envoi et des emplacements de réception pour qu'ils fonctionnent. Vous configurez ces mots de passe dans la boîte de dialogue Propriétés du transport de la console Administration de BizTalk Server pour le port d'envoi ou l'emplacement de réception. Pour obtenir des instructions, consultez [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md). Voir aussi [la création d’un emplacement de réception](../core/how-to-create-a-receive-location.md).  
  
-   **L’hôte doit exister dans le groupe.** Un hôte correspondant à l'hôte spécifié dans les liaisons doit déjà exister dans le groupe BizTalk dans lequel les liaisons sont importées et le niveau de confiance de l'hôte doit correspondre, Dans le cas contraire, l’opération d’importation échoue.  
  
-   **Comportement d’importation dépend de la source des liaisons.** Ces liaisons peuvent avoir été exportées depuis un assembly, une application ou un groupe. L'opération d'importation peut avoir différents effets selon l'emplacement à partir duquel les liaisons ont été exportées. Le tableau suivant récapitule ces différents effets.  
  
    |Origine des liaisons|Importation dans une application|Importation dans un groupe|  
    |----------------------------|-----------------------------------|----------------------------|  
    |Liaisons exportées à partir d'un assembly|L'application spécifiée doit contenir un assembly portant le même nom que l'assembly à partir duquel le fichier de liaison a été exporté, faute de quoi, l'opération d'importation échoue.|Le groupe doit contenir un assembly et une application portant le même nom que l'assembly et l'application à partir desquels le fichier de liaison a été exporté, faute de quoi, l'importation échoue.|  
    |Liaisons exportées à partir d'une application|L'application à partir de laquelle le fichier de liaison a été exporté doit porter le même nom que l'application spécifiée, faute de quoi, l'opération d'importation échoue.|L'application à partir de laquelle le fichier de liaison a été exporté doit porter le même nom qu'une application du groupe dans lequel les liaisons sont importées, faute de quoi, l'opération d'importation échoue.|  
    |Liaisons exportées à partir d'un groupe|Le groupe à partir duquel le fichier de liaison a été exporté doit inclure une application portant le même nom que l'application spécifiée, faute de quoi, l'opération d'importation échoue.|L'importation de liaisons se fait en fonction de correspondances. Autrement dit, les liaisons d'une application faisant partie du groupe à partir duquel les liaisons ont été exportées sont importées dans une application portant le même nom que le groupe actuel.|  
  
-   **L’attribut de nom pour un adaptateur peut être incorrect.** Si le fichier de liaison inclut des paramètres d'adaptateur, vérifiez que l'attribut Nom de l'élément TransportType dans le fichier de liaison est identique à celui configuré pour cet adaptateur dans la console Administration de BizTalk Server (sous Paramètres de plateforme > Adaptateurs).  
  
     En particulier, vous devez vérifier que c’est le cas lors de l’importation des liaisons à partir de [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] à BizTalk Server. Les transports susceptibles de poser problème sont les suivants :  
  
    -   MQS  
  
    -   MSMQ  
  
    -   POP3  
  
    -   Windows SharePoint Services  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment importer des liaisons dans un groupe BizTalk](../core/how-to-import-bindings-into-a-biztalk-group.md)  
  
-   [Comment importer des liaisons dans une Application BizTalk](../core/how-to-import-bindings-into-a-biztalk-application.md)  
  
-   [Comment importer des liaisons pour une Solution EDI-AS2](../core/how-to-import-bindings-for-an-edi-as2-solution.md)