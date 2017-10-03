---
title: "RFC personnalisés utilisés par le fournisseur dans SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Z_EXTRACT_DATA_OO, limitations related to
- RFC, Z_EXTRACT_DATA_OO
- Z_EXTRACT_DATA_OO
- Z_EXTRACT_DATA_OO, best practice
- Z_EXTRACT_DATA_OO, security issue
ms.assetid: 95661f4c-0431-40ca-8a53-3fbe359b8afd
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e55473dbcfeebecc504906d569c129989b054211
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="custom-rfcs-used-by-the-provider-in-sap"></a>RFC personnalisés utilisés par le fournisseur dans SAP
Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] fournit les RFC personnalisés suivants qu’il utilise en interne pour effectuer des opérations sur le système SAP.  
  
-   **Z_EXTRACT_DATA_OO RFC**. L’extraction de données RFC, Z_EXTRACT_DATA_OO, extrait des données à partir des tables ou vues dans le système SAP r/3, convertit les données et retourne les données de façon synchrone dans une table SQL Server ou exporte les données dans un fichier plat. Le Z_EXTRACT_DATA_OO est utilisé pour effectuer une opération SELECT avec les clauses WHERE. Les performances de ce document RFC dépend de votre matériel du système SAP.  
  
     Pour plus d’informations sur la façon dont les types de données .NET et SAP sont mappés pour Z_EXTRACT_DATA_OO RFC, consultez [Data Type Mapping for Custom RFC](../../adapters-and-accelerators/adapter-sap/data-type-mapping-for-custom-rfcs.md).  
  
-   **Z_EXECUTE_SAP_QUERY RFC**. Ce document RFC est utilisée par le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] pour exécuter des requêtes qui sont déjà définis dans le système SAP. Ce document RFC exécute en interne la RFC SAP, RSAQ_REMOTE_QUERY_CALL. Requêtes SAP sont celles créées sous forme graphique à l’aide de l’interface utilisateur graphique SAP en sélectionnant des tables, des colonnes, des paramètres d’entrée, ordre de tri du jeu de résultats, etc.. À l’aide de la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] vous pouvez maintenant exécuter des requêtes de SAP à partir d’un client d’ADO.NET.  
  
     Les valeurs retournées par l’opération EXECQUERY sont de type chaîne.  
  
## <a name="limitations-related-to-the-zextractdataoo-rfc"></a>Limitations relatives à la RFC Z_EXTRACT_DATA_OO  
  
-   Le document RFC Z_EXTRACT_DATA_OO prend en charge la lecture des données à partir des tables qui répondent aux conditions suivantes :  
  
    -   TabClass pour la table est TRANSP, cluster ou POOL.  
  
    -   TabClass est la vue et ViewClass D ou P.  
  
-   Z_EXTRACT_DATA_OO ne prend pas en charge les tables de cluster de ressources humaines, par exemple PCL1, PCL2, PCL3, PCL4, PCL5.  
  
-   Le nombre de lignes qui peuvent être extraites par Z_EXTRACT_DATA_OO varie selon les ressources matérielles sur le serveur SAP.  
  
-   Toutes les données extraites est retourné dans l’ordre des clés primaires.  
  
-   Tables ou vues contenant les types de données de longueur variable de chaîne, SSTRING et RAWSTRING ne sont pas pris en charge. Tables ou vues contenant ces types de données ne peut pas être extrait.  
  
-   Z_EXTRACT_DATA_OO exécute issues de la conversion de tous les champs qui ont des sorties de conversion assignés à. Les valeurs converties résultants doivent être entrées dans la clause WHERE d’une instruction SELECT. Valeurs converties sont retournés. Cela peut provoquer des incohérences entre les résultats retournés par Z_EXTRACT_DATA_OO et les résultats retournés dans l’Explorateur de données SAP (SE16).  
  
-   Les tables sélectionnées ne peut pas contenir de noms de champs qui sont des noms réservés dans ABAP (par exemple, la connexion).  
  
-   En raison d’une limitation dans le processeur de requêtes dans r/3 SAP version 4 .6C, les valeurs des champs d’entier de type INT4 doit être supérieur ou égal à-999999999 dans la clause WHERE. Lignes avec des valeurs INT4-999999999 inférieure ne seront pas extraites que le champ qui contient la valeur est sélectionné.  
  
-   Types de valeurs pour toutes les données dans une clause WHERE sont limités à 256 caractères lors de l’exécution sur SAP système 4.7 ou version ultérieure ; la limite est de version 4 .6C 70 caractères. Pour les valeurs de type de données brutes, ces limites sont divisés par deux à 128 et 35 caractères, respectivement. Il n’existe aucune limite sur la longueur du type de données RAW et LCHR lorsqu’ils sont retournés en conséquence.  
  
-   Dans r/3 SAP version 4 .6C, les champs dont la clause sont limités à 70 caractères.  
  
-   SAP r/3 version 4 .6C, une table avec un champ de clé primaire qui a une longueur supérieure à 70 caractères de la sortie ne peut pas être extrait.  
  
-   Dans SAP r/3, version 4 .6C, tables et des vues qui contiennent des types de données de longueur variable (`VARC`) ne sont pas pris en charge et les tables et vues contenant ces types de données ne peut pas être extraites de la source de données à l’aide de l’appel de fonction Z_EXTRACT_DATA_OO.  
  
-   En mode de fichier, l’appel de fonction Z_EXTRACT_DATA_OO ne vérifie pas si un fichier de destination est déjà ouverte, lui-même ou par une autre application. Par conséquent, la fonction peut écrire incorrectement un fichier ouvert lors de l’ajout simultanément des données dans le même fichier. Aucune erreur n’est générée.  
  
-   En mode de fichier, l’appel de fonction Z_EXTRACT_DATA_OO peut remplacer les fichiers existants. Assurez-vous que les utilisateurs SAP utilisent Z_EXTRACT_DATA_OO du système de fichiers à accès limité par S_DATASET.  
  
## <a name="security-considerations-with-the-custom-rfc"></a>Considérations de sécurité avec le RFC personnalisé  
  
-   `Security Issue`: Il est potentiels pour exposer des données sont écrites dans les fichiers plats, si vous ne pas protéger ces fichiers.  
  
     `Best practice`: Améliorer la sécurité du partage de fichiers auquel toutes les données sont écrites par l’appel de fonction Z_EXTRACT_DATA_OO en mode de fichier plat.  
  
-   `Security Issue`: Il existe un risque pour remplacer les fichiers sur un partage qui est écrit à l’aide de l’appel de fonction Z_EXTRACT_DATA_OO en mode de fichier. Cela peut se produire à n’importe quel fichier sur un partage auquel le compte de domaine SAP a accès.  
  
     `Best practice`: S’efforcent de protéger tous les partages à laquelle le compte de domaine SAP a accès.  
  
-   `Security Issue`: Les utilisateurs ont la possibilité à inspecter (ou « espionne ») des données lors de leur transmission à partir d’un serveur d’applications SAP à son partage de fichiers cible, dans les cas où la cible se trouve sur un autre ordinateur physique.  
  
     `Best practice`: Permet d’utiliser IPsec ou une autre méthode appropriée pour aider à renforcer la communication entre le serveur SAP et de ses cibles.  
  
## <a name="see-also"></a>Voir aussi  
 [Sur le fournisseur de données .NET Framework pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)