---
title: "L’importation d’un PIP basé sur XSD | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PIPs, importing
- XSD-based PIPs
- PIPs, XSD-based PIPs
ms.assetid: d12441d4-79bf-4c24-9360-4b78c1da0d34
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d8865d7a75bdb06895b963b8269ed457cd5804f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="importing-an-xsd-based-pip"></a>Importation d'un PIP basé sur XSD
Alors que la majorité des PIP fournis par RosettaNet.org est basée sur DTD, les PIP les plus récents sont basés sur XSD. La procédure suivante montre comment importer des PIP basés sur XSD.  
  
### <a name="to-import-an-xsd-based-pip"></a>Pour importer un PIP basé sur XSD  
  
1.  Téléchargez le fichier .zip du PIP basé sur XSD à partir de RosettaNet.org à l'adresse [http://go.microsoft.com/FWLink/?LinkID=33859](http://go.microsoft.com/FWLink/?LinkID=33859) ou à partir de CIDX.org à l'adresse [http://go.microsoft.com/FWLink/?LinkID=33859](http://go.microsoft.com/FWLink/?LinkID=62361). Extrayez les fichiers du fichier .zip. Les fichiers dont vous avez besoin se trouvent dans les sous-dossiers du dossier XML.  
  
2.  Ouvrez Visual Studio. Créez un projet BizTalk.  
  
3.  Ouvrez l'Explorateur Windows, puis accédez au dossier XML extrait à l'étape 1. Sélectionnez le premier dossier sous le dossier XML, faites-le glisser vers l'Explorateur de solutions dans Visual Studio, puis déposez-le dans votre projet. Répétez l'opération pour chacun des sous-dossiers du dossier XML, en créant la même structure de dossier dans votre projet.  
  
    > [!NOTE]
    >  Pour un PIP PIP7c7, ces dossiers incluent les dossiers Domain, Interchange, System et Universal. Pour ce PIP, votre projet doit contenir les dossiers Domain, Interchange, System et Universal, ainsi que leur contenu.  
  
4.  Si le dossier système contient un fichier .xsd, sélectionnez ce fichier dans l'Explorateur de solutions et modifiez l'espace de noms répertorié dans la page de propriétés de façon à ce qu'il ne contienne pas la chaîne « .System ». Par exemple, pour le PIP PIP7c7, vous pouvez modifier l'espace de noms pour obtenir « PIP7c7._System ». Répétez l'opération pour chaque fichier .xsd situé dans le dossier System. Si vous ne modifiez pas l'espace de noms, vous recevrez l'erreur suivante ou une erreur similaire :  
  
    ```  
    The type or namespace name 'SerializableAttribute' does not exist in the class or namespace 'PIP7C7.System'.  
    ```  
  
5.  Passez en revue tous les fichiers .xsd pour vous assurer que le \<schéma\> type du nœud racine et le nom de type ne sont pas identiques. Par exemple, pour un PIP pip7c7, le fichier partneridentification.xsd situé dans le dossier Universal a le nom de « PartnerIdentification » à la fois pour le \<schéma\> (lorsque PartnerIdentification.xsd est sélectionné dans l’Explorateur de solutions) et également le Nœud de racine PartnerIdentification. Pour corriger ce problème, sélectionnez PartnerIdentification.xsd dans l'Explorateur de solutions, puis, dans la page de propriété, modifiez la propriété TypeName afin qu'elle ne contienne pas le même nom de type que le nœud racine PartnerIdentification. Par exemple, remplacez le nom de type pour qu'il soit « _PartnerIdentification ». Si vous n'effectuez pas cette étape, vous recevez l'erreur suivante lorsque vous essayez de générer le projet :  
  
    ```  
    Node "<Schema>" - This schema file has a TypeName that collides with the RootNode TypeName of one of its root Nodes. Make sure that they are different.  
    ```  
  
    > [!NOTE]
    >  La colonne File dans la liste d'erreurs indique quels fichiers subissent ce problème.  
  
6.  Générez et déployez le projet.