---
title: "Planification de la création du schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ecb9154-b457-4209-b9b9-572c186bf5e7
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60fc7a3cafb3f13a189383df70d4b9ea0bf98f54
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-schema-creation"></a>Planification de la création de schémas
On utilise des schémas pour valider les instances de messages destinés à être conformes au schéma, pour définir la manière dont les messages d'instance de divers format (XML et non XML) peuvent être convertis dans les deux sens, et pour définir comment les messages d'instance XML dotés d'une structure peuvent être transformés en messages d'instance XML dotés d'une autre structure. Pour plus d’informations sur la distinction entre la conversion et la transformation des messages d’instance, consultez [vs de Transformation. Traduction](../core/data-transformation.md).  
  
 Le tableau suivant présente certaines des questions auxquelles vous devez répondre au moment de planifier la création de schémas dans l'Éditeur BizTalk.  
  
|Question relative à la planification|Recommandation|  
|-----------------------|--------------------|  
|Quels schémas dois-je créer ?|Dressez la liste des documents commerciaux que vous traiterez à l'aide de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Votre liste peut contenir des documents tels qu'un bon de commande, une facture, une confirmation d'expédition, etc. Elle peut également comprendre plus d'un exemplaire de chaque document commercial, par exemple si la structure d'un bon de commande reçu d'un partenaire commercial est différente de celle d'un bon de commande reçu d'un autre partenaire commercial.|  
|Les documents que j'envoie et reçois existent-ils déjà au format XML ?|Ajoutez à votre liste des informations relatives au format (XML et autres formats de fichiers plats positionnels ou délimités) de chaque document commercial que vous envoyez ou recevez.|  
|Quels points de départ sont disponibles dans ma liste pour la création de schémas ?|Si elle s'avère parfois nécessaire, la création de schémas est plus ardue que la génération de schémas à partir de l'une des sources prises en charge. Si votre schéma est déjà représenté avec le langage XSD (XML Schema definition), aucune génération n'est nécessaire. Il vous suffit de l'ouvrir dans l'Éditeur BizTalk.<br /><br /> Si vous disposez d'un message d'instance XML bien formé, d'une représentation de définition de type de document (DTD) de votre schéma ou d'une représentation XDR (XML-Data Reduced), vous pouvez automatiquement générer votre schéma. Il vous faudra peut-être affiner le schéma généré à l'aide de l'Éditeur BizTalk mais vous y gagnerez quand même. Pour obtenir des instructions, consultez la procédure « pour générer un schéma à partir d’une source non XSD » dans [création de schémas pour les Messages XML](../core/how-to-create-schemas-for-xml-messages.md).<br /><br /> Si aucun de ces points de départ n'est à votre disposition pour un ou plusieurs des documents commerciaux de votre liste, vous devrez créer un schéma à l'aide de l'Éditeur BizTalk et définir sa structure.|  
  
## <a name="see-also"></a>Voir aussi  
 [Comment créer des schémas pour les Messages XML](../core/how-to-create-schemas-for-xml-messages.md)   
 [Création de schémas à l’aide de l’Éditeur BizTalk](../core/creating-schemas-using-biztalk-editor.md)