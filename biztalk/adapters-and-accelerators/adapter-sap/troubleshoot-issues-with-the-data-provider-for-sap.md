---
title: "Résoudre les problèmes avec le fournisseur de données pour SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Provider for SAP, troubleshooting
- troubleshooting, Data Provider for SAP
ms.assetid: 6fe9baed-0404-4f15-b76e-88cc11c5ff46
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba61b75f95fad429c70da42479f22a32fa4e5a65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-issues-with-the-data-provider-for-sap"></a>Résoudre les problèmes avec le fournisseur de données pour SAP
Cette section présente l’utilisation de techniques de dépannage pour résoudre les erreurs de fonctionnement que vous pouvez rencontrer lorsque vous utilisez [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)].  
  
##  <a name="BKMK_SAPUnknownParam"></a>Erreur de paramètre à l’aide du fournisseur de données pour SAP  
 **Problème**  
  
 Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] attribue l’erreur suivante :  
  
```  
Microsoft.Data.SAPClient.SAPException: Failed to retrieve data from SAP server --- > Microsoft.ServiceModel.Channels.Common.XmlReaderParsingException: Unknown Parameter OUT_ZDATATABLE.  
```  
  
 **Cause**  
  
 Les RFC personnalisé, Z_EXTRACT_DATA_OO, installé dans votre système SAP n’est pas la plus récente. Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] utilise un RFC personnalisé, Z_EXTRACT_DATA_OO, pour effectuer des opérations SELECT sur la table SAP.  
  
 **Résolution**  
  
 Vous devez mettre à jour le RFC personnalisé à la dernière version disponible. Cette RFC, le Z_EXTRACT_DATA_OO, est disponible avec l’adapterpacknoversion. Pour plus d’informations sur la façon d’installer et désinstaller le RFC personnalisé, consultez [installer les RFC personnalisés pour le fournisseur de données pour SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).
  
##  <a name="BKMK_SAPOOM"></a>Exceptions de mémoire insuffisante lors de la sélection des données à partir d’une table SAP  
 **Problème**  
  
 Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] lève une exception de mémoire hors lors de la sélection des données à partir d’un système SAP.  
  
 **Cause**  
  
 Par défaut, le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] récupère les 10 000 lignes à la fois. En outre, chaque lot de lignes récupérées à partir du système SAP est stocké dans la mémoire. Par conséquent,  
  
-   Si la table qui sont en cours extraites des données contient un grand nombre de lignes, ou  
  
-   Si la table contient des colonnes de types de données qui consomment une quantité importante de mémoire,  
  
 La consommation de mémoire par les [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] augmente considérablement et peut entraîner une absence d’exception de mémoire.  
  
 **Résolution**  
  
 Vous pouvez modifier le nombre maximal de lignes récupérées à partir du système SAP. Vous pouvez le faire en spécifiant une option 'batchsize' avec l’instruction SELECT. Exemple :  
  
```  
SELECT * FROM <tablename> OPTION 'batchsize 1000'  
```  
  
 Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] maintenant récupère uniquement les 1000 lignes à la fois et donc ne pas utiliser de grande quantité de mémoire.  
  
##  <a name="BKMK_SAPQueryExcep"></a>Exception lors de l’exécution d’une requête qui accepte des paramètres avec des valeurs de date  
 **Problème**  
  
 Vous obtenez l’exception suivante lorsque vous exécutez une requête à l’aide de la commande EXECQUERY qui a un paramètre qui accepte une valeur de date :  
  
```  
ErrorCode=RFC_SYS_EXCEPTION. ErrorGroup=RFC_ERROR_SYSTEM_FAILURE.   
SapErrorMessage=Enter date in the format __.__.____.  
```  
  
 **Cause**  
  
 Lors de l’exécution de requêtes à l’aide de la commande EXECQUERY, vous devez toujours spécifier les valeurs de date au format AAAAMMJJ.  
  
 **Résolution**  
  
 Assurez-vous que vous spécifiez des valeurs de date au format AAAAMMJJ. Exemple :  
  
```  
EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1='20080606'  
```  
  
##  <a name="BKMK_SAPNOVARIANT"></a>Exception NO_VARIANT l’exécution de requêtes à l’aide de la commande EXECQUERY  
 **Problème**  
  
 Vous obtenez l’exception suivante lorsque vous exécutez une requête à l’aide de la commande EXECQUERY :  
  
```  
Exception: Details: ErrorCode=RFC_EXCEPTION. ErrorGroup=RFC_ERROR_APPLICATION_EXCEPTION. SapErrorMessage=NO_VARIANT.  
AdapterErrorMessage=Error returned by RfcCallReceiveEx while calling RFC: <RFC name>  
```  
  
 **Cause**  
  
 Il peut y avoir deux causes probables de cette exception :  
  
1.  La requête que vous essayez d’exécuter a variantes définis dans le système SAP. Variantes de faire référence à un jeu de critères de sélection que vous pouvez spécifier lors de l’exécution d’une requête SAP enregistré. Par exemple, vous pouvez utiliser les variantes pour spécifier les valeurs par défaut pour les requêtes.  
  
2.  La requête que vous essayez d’exécuter aucune des deux a une variante définie ni il attend une valeur de paramètre à passer.  
  
 **Résolution**  
  
1.  Pour une raison 1, assurez-vous que vous spécifiez le nom de la variante associé à la requête. Exemple :  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @variant =  ‘variant1’  
    ```  
  
2.  Pour une raison 2, assurez-vous que vous fournissez un nom de paramètre factice et la valeur lors de la spécification de la commande de requête. Par exemple, si « myquery » requête ne nécessite pas de n’importe quel paramètre à exécuter, la commande EXECQUERY doit être spécifiée en tant que :  
  
    ```  
    EXECQUERY myquery @usergroup='mygroup',@P1 = 'dummy_value'  
    ```  
  
## <a name="see-also"></a>Voir aussi  
[Résoudre les problèmes de l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)