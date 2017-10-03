---
title: "Comment étendre l’Assistant génération de schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- utilities, Schema Generator Wizard
- Schema Generator Wizard
ms.assetid: ea4b5532-f904-4da0-9612-e092e7e4edc1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 11db44e07191b0996043dd6b819ef2ba9162a0e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-extend-the-schema-generator-wizard"></a>Comment étendre l’Assistant génération de schéma
Comment étendre l’Assistant génération de schémas et comment créer un nouvel Assistant de génération de schéma.  
  
## <a name="extend-the-existing-schema-wizard"></a>Étendre l’Assistant schéma existant  
  
1.  Implémentez l’interface ISchemaGenerator pour créer un nouveau module de génération de schéma que vous pouvez intégrer à l’Assistant génération de schémas.  
  
    ```  
    public interface ISchemaGenerator  
    {  
    //Method to extract a schema from a document.  
    void GenerateSchema(string inputDocument,string outputDocumentPath);  
  
    //Method to extract the errors.  
    [return : MarshalAs(UnmanagedType.SafeArray, SafeArraySubType = VarEnum.VT_VARIANT )]object [] Errors();  
  
    //Method to extract the warnings.  
    [return : MarshalAs(UnmanagedType.SafeArray, SafeArraySubType = VarEnum.VT_VARIANT )]object [] Warnings();  
  
    //Method to extract the referenced schemas.  
    [return : MarshalAs(UnmanagedType.SafeArray, SafeArraySubType = VarEnum.VT_VARIANT )]object [] ReferencedSchemas();  
    }  
    ```  
  
2.  Déposez l'assembly généré dans le dossier d'installation Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] suivant :  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Extensions de l’éditeur \Developer Tools\Schema  
  
     La prochaine fois que vous exécuterez l'Assistant Génération de schémas, il utilisera automatiquement le nouveau module de génération de schémas.  
  
 Effectuez la procédure ci-dessous pour créer un Assistant Schéma.  
  
 **Emplacement dans le Kit de développement logiciel**  
  
 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Générateur de \SDK\Utilities\Schema  
  
### <a name="create-a-new-schema-wizard"></a>Assistant Création d’un nouveau schéma  
  
1.  Exécutez InstallDTD.vbs pour installer le fichier Microsoft.BizTalk.DTDToXSDGenerator.dll dans [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Developer Tools\Schema Extensions de l’éditeur. DTDToXSDGenerator.dll présente les classes que vous pouvez utiliser pour convertir des fichiers DTD en fichiers XSD.  
  
2.  Exécutez InstallWFX.vbs pour installer le fichier Microsoft.BizTalk.WFXToXSDGenerator.dll dans [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Developer Tools\Schema Extensions de l’éditeur. WFXToXSDGenerator.dll présente les classes que vous pouvez utiliser pour convertir les fichiers WFX en fichiers XSD.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaires dans le Kit de développement](../core/utilities-in-the-sdk.md)