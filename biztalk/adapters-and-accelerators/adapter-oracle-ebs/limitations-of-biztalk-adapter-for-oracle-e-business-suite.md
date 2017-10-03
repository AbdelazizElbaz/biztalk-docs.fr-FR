---
title: "Limitations de l’adaptateur BizTalk pour Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 149cee03-43cd-4cb3-a937-6565f5e96ce5
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e7611c56fbd24c7c7cf09d38d376df585b72b284
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="limitations-of-biztalk-adapter-for-oracle-e-business-suite"></a>Limitations de l’adaptateur BizTalk pour Oracle E-Business Suite
## <a name="general-limitations"></a>Limitations générales  
 Les éléments suivants sont connus limitations pour [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]:  
  
-   Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne prend pas en charge la passerelle XML, file d’attente avancée et les événements de l’entreprise.  
  
     Toutefois, vous pouvez contourner la limitation des événements commerciaux de la manière suivante :  
  
    1.  Dans Oracle Business événements système, créez un abonnement pour appeler une procédure PL/SQL personnalisée lorsqu’un événement se produit.  
  
    2.  Écrire une procédure PL/SQL personnalisée qui reçoit l’événement de l’entreprise.  
  
    3.  Utilisez la procédure PL/SQL personnalisée pour stocker les données résultantes (événement et la charge utile d’événement) dans une table.  
  
    4.  Utilisez le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour interroger ou de recevoir des notifications à partir de la table.  
  
-   Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne prend pas en charge les Types XML.  
  
-   Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne pas autoriser les clients à définir la valeur du premier élément dans un VARRAY avec la valeur NULL.  
  
-   Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne pas les enregistrements de prise en charge qui contiennent des champs de type de tables PL/SQL de type d’enregistrement.  
  
-   Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne prend pas en charge les Types définis par l’utilisateur (UDT) qui ont des références circulaires.  
  
-   Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne prend pas en charge le type de données BFILE à l’intérieur des types complexes (telles que l’enregistrement type, TABLE type, UDT et VARRAY).  
  
-   Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge jusqu'à deux niveaux d’imbrication des UDT.  
  
-   À l’exception des tables de PL/SQL, le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne prend pas en charge les UDT sont définis à l’intérieur d’un package.  
  
-   Lorsque l’utilisation des adaptateurs dans BizTalk Server, si les informations d’identification sur WCF-custom port d’envoi sont incorrectes, les messages de demande ne sont pas traités. Après avoir spécifié les informations d’identification correctes, le message est envoyé pour Oracle E-Business Suite et une réponse est reçue. Toutefois, le message de réponse n’est pas disponible pour le port de sortie. Dans de tels scénarios, vous devrez peut-être redémarrer l’instance d’hôte.  
  
## <a name="limitations-due-to-odpnet"></a>Limitations en raison de ODP.NET  
 Les éléments suivants sont connus limitations pour [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] en raison de la limitation de ODP.NET :  
  
-   Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne prend pas en charge les tables PL/SQL qui ne sont pas indexés par un champ numérique.  
  
-   Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne prend pas en charge les tableaux associatifs qui ne contiennent pas de n’importe quel élément.  
  
-   Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne prend pas en charge les UDT qui contiennent le type de données TimeStamp avec les attributs de fuseau horaire local (TimeStampLTZ).  
  
-   Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne prend pas en charge les UDT qui contiennent un «. » (point) dans leurs noms.  
  
-   Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne prend pas en charge les UDT qui contiennent des types de données objet BLOB, CLOB et NCLOB en tant que paramètre IN OUT.  
  
-   Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne prend pas en charge Varray de Varray des types simples suivants : BFILE, IntervalDS, IntervalYM, TimeStampLTZ et TimeStampTZ.  
  
-   En raison de la limitation d’associatifs, les tables de PL/SQL ou PL/SQL d’enregistrements qui contiennent un des types de données suivants ne sont pas gérées dans le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]:  
  
    -   BFILE  
  
    -   BLOB  
  
    -   CLOB  
  
    -   IntervalDS  
  
    -   IntervalYM  
  
    -   Long  
  
    -   NCLOB  
  
    -   ID de ligne  
  
    -   TimeStamp  
  
    -   TimeStampLTZ  
  
    -   TimeStampTZ  
  
## <a name="see-also"></a>Voir aussi  
 [Comprendre l’adaptateur BizTalk pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)