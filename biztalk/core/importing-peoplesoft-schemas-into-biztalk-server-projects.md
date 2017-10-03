---
title: "Importation des schémas PeopleSoft dans des projets BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- generating schemas
- schemas, generating
- schemas, importing into BizTalk Server projects
- component interfaces
- BizTalk Server, schemas [PeopleSoft]
- importing schemas into BizTalk Server
ms.assetid: 411f25f4-4431-44e4-84cf-5c515b3e32db
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b4946b438adc0d1e4d360b35207ff69e85b4e2c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="importing-peoplesoft-schemas-into-biztalk-server-projects"></a>Importation des schémas PeopleSoft dans des projets BizTalk Server
Après avoir créé le système PeopleSoft Enterprise, vous pouvez accéder au serveur qui lui est associé et importer des schémas dans un projet BizTalk Server.  
  
## <a name="browsing-a-peoplesoft-server-system"></a>Accès à un système serveur de PeopleSoft  
 L'Assistant Adaptateur permet d'accéder à un serveur de PeopleSoft  
  
#### <a name="to-browse-a-peoplesoft-server-system"></a>Pour accéder à un système serveur de PeopleSoft  
  
1.  Cliquez avec le bouton droit sur un projet BizTalk Server, puis sélectionnez l'une des options suivantes.  
  
    -   Si vous avez déjà un schéma généré pour votre objet, sélectionnez **ajouter**, cliquez sur **ajouter un schéma,** , puis sélectionnez le schéma existant à ajouter à votre orchestration.  
  
    -   Si vous ne disposez pas d’un schéma généré pour votre objet, sélectionnez **ajouter**, puis cliquez sur **ajouter les éléments générés**, puis sélectionnez la carte. Ceci est le même nom que celui entré dans le **AdapterProperties** boîte de dialogue. Pour plus d'informations, consultez la rubrique « Boîte de dialogue Propriétés de l'adaptateur » dans l'aide principale de BizTalk.  
  
2.  Cliquez sur Suivant.  
  
     Le système PeopleSoft Enterprise s'affiche dans l'Explorateur.  
  
     ![](../core/media/psad-psnewadapter-14-browsing-cominterfacess.gif "PSAd_PSNewAdapter_14_Browsing_ComInterfacess")  
  
### <a name="component-interfaces"></a>Interfaces de composant  
 Dans le **Interfaces de composant** (CI), dossier, vous pouvez afficher toutes les interfaces de composant disponible dans le système. Une interface de composant déclare l'ensemble des méthodes et des propriétés qu'elle prend en charge. Elle n'implémente aucun comportement ni propriété. L'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise expose des méthodes standard (par exemple, CreateEx, DeleteOnly, Find, Get et UpdateEx). Pour obtenir une description de ces méthodes, consultez [annexe a : composant Interface méthodes](../core/appendix-a-component-interface-methods.md).  
  
## <a name="generating-schemas"></a>Création de schémas  
 Effectuez ces étapes pour générer des schémas.  
  
#### <a name="to-generate-the-schemas"></a>Pour créer les schémas  
  
-   Sélectionnez l’élément pour lequel vous souhaitez importer des schémas : un **Message**, **requête**, ou **Interface de composant**.  
  
     BizTalk Server génère les schémas pour l'élément sélectionné et les importe dans un projet BizTalk Server.  
  
    > [!NOTE]
    >  Si les définitions de l'objet serveur sont modifiées, vous devez recréer le schéma afin de mettre à jour les données qu'il contient.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de gestionnaires d’envoi PeopleSoft](../core/creating-peoplesoft-send-handlers.md)