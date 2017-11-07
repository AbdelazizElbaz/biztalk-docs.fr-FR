---
title: "Importer des schémas PeopleSoft dans Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 411f25f4-4431-44e4-84cf-5c515b3e32db
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6af82459f8b51f3dfa73a52593db18d25365c2a
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="import-peoplesoft-schemas-into-biztalk-server-projects"></a>Importer des schémas PeopleSoft dans des projets BizTalk Server
Après avoir créé le système PeopleSoft Enterprise, vous pouvez accéder au serveur qui lui est associé et importer des schémas dans un projet BizTalk Server.  
  
## <a name="browse-a-peoplesoft-server-system"></a>Accéder à un système de serveur de PeopleSoft  
  
1.  Cliquez avec le bouton droit sur un projet BizTalk Server, puis sélectionnez l'une des options suivantes.  
  
    -   Si vous avez déjà un schéma généré pour votre objet, sélectionnez **ajouter**, cliquez sur **ajouter un schéma,** , puis sélectionnez le schéma existant à ajouter à votre orchestration.  
  
    -   Si vous ne disposez pas d’un schéma généré pour votre objet, sélectionnez **ajouter**, puis cliquez sur **ajouter les éléments générés**, puis sélectionnez la carte. Ceci est le même nom que celui entré dans le **AdapterProperties** boîte de dialogue. Pour plus d'informations, consultez la rubrique « Boîte de dialogue Propriétés de l'adaptateur » dans l'aide principale de BizTalk.  
  
2.  Cliquez sur Suivant.  
  
     Le système PeopleSoft Enterprise s'affiche dans l'Explorateur.  
  
     ![](../core/media/psad-psnewadapter-14-browsing-cominterfacess.gif "PSAd_PSNewAdapter_14_Browsing_ComInterfacess")  
  
### <a name="component-interfaces"></a>Interfaces de composant  
 Dans le **Interfaces de composant** (CI), dossier, vous pouvez afficher toutes les interfaces de composant disponible dans le système. Une interface de composant déclare l'ensemble des méthodes et des propriétés qu'elle prend en charge. Elle n'implémente aucun comportement ni propriété. L'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise expose des méthodes standard (par exemple, CreateEx, DeleteOnly, Find, Get et UpdateEx). Pour obtenir une description de ces méthodes, consultez [annexe a : composant Interface méthodes](../core/appendix-a-component-interface-methods.md).  
  
## <a name="generate-schemas"></a>Générer des schémas  
  
Sélectionnez l’élément pour lequel vous souhaitez importer des schémas : un **Message**, **requête**, ou **Interface de composant**.  BizTalk Server génère les schémas pour l'élément sélectionné et les importe dans un projet BizTalk Server.  
  
> [!NOTE]
>  Si les définitions de l'objet serveur sont modifiées, vous devez recréer le schéma afin de mettre à jour les données qu'il contient.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de gestionnaires d’envoi PeopleSoft](../core/creating-peoplesoft-send-handlers.md)