---
title: "Distribuer des certificats numériques | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- digital signatures
- security, digital signatures
ms.assetid: 3e93a405-3c9b-43f5-bbdf-bec25d43eb45
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 486a1f45dc6a570bab6518eef215f4133015ead5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="distributing-digital-certificates"></a>Distribuer des certificats numériques
Utilisé pour la signature numérique des certificats numériques sont généralement émis et distribués aux stations de travail utilisateur par les autorités de certification (CA), soit les entités commerciales externes telles que VeriSign ou les autorités de certification internes hébergé dans une organisation. Les types (algorithmes de chiffrement et les niveaux de chiffrement) de certificats numériques sont utilisés peuvent différer d’une organisation à l’autre. [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]signer numériquement un formulaire à l’aide de n’importe quel format de certificat qui est constitué d’une clé privée et qui possède une Signature numérique ou une valeur pour l’attribut utilisation de la clé de chiffrement. En outre, l’objectif du certificat doit être défini en tant que l’authentification du Client.  
  
 Est de l’objectif principal d’un certificat numérique pour identifier l’utilisateur qui a utilisé ce certificat pour signer numériquement un document et créer un hachage unidirectionnel chiffré des données de document. Les données de hachage chiffré détecte les modifications apportées aux données après la signature (si les données ont changé, il ne produit pas le même hachage). Les certificats numériques sont émis basée sur des rôles et des comptes d’utilisateur de domaine (ou [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] groupes de domaine), et sont spécifiques à l’utilisateur protégées par [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] des mécanismes d’ouverture de session utilisateur et l’authentification. Vous pouvez signer numériquement des documents uniquement à l’aide de certificats numériques émis spécialement pour vous, en fonction de votre [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] compte d’utilisateur de domaine.  
  
 Les solutions SWIFT [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms générés avec l’utilitaire FormGenerator fournie par A4SWIFT vous obliger à signer numériquement (ou contresigner) le formulaire chaque fois que vous essayez d’envoyer le message à A4SWIFT Message Repair et New Submission (via [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)]). Vous ne pouvez pas contourner cette exigence dans [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]. Toutefois, vous pouvez accéder [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] complètement et l’écriture des messages directement vers les dossiers SharePoint Web (en supposant que vous avez les informations d’identification appropriées pour accéder aux dossiers SharePoint Web). Toutefois, si le message ne contient pas une signature numérique valide, Message Repair et New Submission immédiatement rejette le message comme une erreur de sécurité.  
  
 Les composants de Message réparer et New Submission doivent avoir accès à la clé publique du certificat numérique utilisé dans le message à réparer le flux de travail. Pour activer l’accès Message Repair et New Submission à la clé publique, les certificats pour chaque utilisateur doit résider dans le magasin autres personnes sur la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] ordinateurs hébergeant le service d’orchestration Message Repair et New Submission.  
  
> [!NOTE]
>  Le certificat utilisé dans le flux de travail de réparation de Message et New Submission et réparation de message de configuration utilisateur doit être émise par une autorité de certification de confiance, telles que VeriSign ou e-Trust.  
  
 Pour obtenir des informations spécifiques sur la façon de configurer les autorités de certification internes, consultez le « paramètre d’une autorité de certification » sur le site Web MSDN à l’adresse [http://go.microsoft.com/fwlink/?LinkId=48688](http://go.microsoft.com/fwlink/?LinkId=48688).