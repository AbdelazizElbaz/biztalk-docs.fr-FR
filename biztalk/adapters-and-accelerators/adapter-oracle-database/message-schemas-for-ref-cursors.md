---
title: "Schémas de message pour REF CURSOR | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- REF CURSORS, message schemas for
- IN REF CURSOR
- OUT REF CURSOR
- IN OUT REF CURSOR
ms.assetid: b62e7a9f-278c-41b3-90f0-2f621a34327b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9bddfde0b0897c7d8c21a20126d2fa1d2f0f8c78
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-ref-cursors"></a>Schémas de message pour REF CURSOR
Un REF CURSOR est un type de données Oracle PL/SQL qui représente un pointeur vers un jeu de résultats dans la base de données Oracle. Types de REF CURSOR activer l’entrée et de sortie de diffusion en continu de données et sont idéaux pour le transfert de grandes quantités de données vers et depuis un bloc de code PL/SQL. [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]prend en charge en passant les paramètres REF CURSOR fortement typée et faiblement typée procédures PL/SQL et les fonctions, OUT et dans les paramètres.  
  
 Dans la base de données Oracle, un type de REF CURSOR peut être soit fortement typée ou faiblement typé :  
  
-   REF CURSOR fortement typée est déclaré avec une clause RETURN comme dans `TYPE StrongCurType IS REF CURSOR RETURN emp%ROWTYPE;`. Une variable de REF CURSOR fortement typé peut représenter uniquement un jeu de résultats qui contient des données qui correspond au type avec lequel son type REF CURSOR est déclaré. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] renvoie un résultat fortement typée pour REF CURSOR fortement typée.  
  
-   REF CURSOR faiblement typée est déclaré sans clause de retour comme dans `TYPE WeakCurType IS REF CURSOR;`. Oracle fournit également un type spécial de REF CURSOR appelé SYS_REFCURSOR qui peut être utilisé pour déclarer des variables de REF CURSOR faiblement typée. Variables de REF CURSOR faiblement typée peuvent représenter un jeu de résultats contenant n’importe quel type de données de ligne. La [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] retourne un jeu de résultats de faiblement typé d’enregistrements génériques pour REF CURSOR faiblement typée.  
  
## <a name="in-ref-cursor-parameters"></a>DANS les paramètres REF CURSOR  
 Il n’existe aucune API ODP.NET pour créer un REF CURSOR sur le serveur Oracle, donc la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ne peut pas fournir la capacité d’un programme client créer et gérer les variables de REF CURSOR.  
  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] est le cas, toutefois, activer un client de passer des paramètres IN REF CURSOR à des fonctions ou des procédures stockées en spécifiant un bloc de code PL/SQL qui retourne les REF CURSOR. L’adaptateur utilise ce code pour créer et ouvrir une variable REF CURSOR sur le serveur Oracle ; Ensuite, il appelle la fonction ou procédure stockée utilisant cette variable en tant que paramètre IN.  
  
 La [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] représente des paramètres IN REF CURSOR en tant que chaînes contenant le bloc de code PL/SQL. Dans ce bloc, l’emplacement du curseur REF est spécifié avec un point d’interrogation ( ?). Le bloc de code PL/SQL peut contenir une instruction OPEN-FOR qui contient une requête SQL ; ou elle peut contenir un appel de fonction ou une procédure dans laquelle un REF CURSOR ouverte est retourné dans un paramètre OUT.  
  
 Voici comment spécifier un en REF CURSOR en appelant une procédure stockée ou une fonction pour ouvrir le REF CURSOR.  
  
```  
<[IN_REF_CURSOR_PARAM_NAME]>begin [SP_NAME]([SP_PARAMS...], ?, [SP_PARAMS...]); end;</[IN_REF_CURSOR_PARAM_NAME]>  
  
Example:  
<EMP_RC>begin GETEMP(1, ?); end; </EMP_RC>  
```  
  
 Voici comment spécifier un en REF CURSOR à l’aide d’une requête SELECT pour ouvrir le REF CURSOR.  
  
```  
<IN_REF_CURSOR_PARAM_NAME>begin open ? for select [FIELD_NAMES] from [TABLE_NAME]; end;</IN_REF_CURSOR_PARAM_NAME>  
  
Example:  
<EMP_RC>begin open ? for select * from EMP; end;</EMP_RC>  
```  
  
## <a name="out-ref-cursor-parameters"></a>LES paramètres REF CURSOR  
 LES REF CURSOR paramètres sont retournés sous la forme des jeux de résultats de fortement typée ou faiblement typée. Le type de jeu de résultats retourné dépend de si le paramètre REF CURSOR est déclaré comme un REF CURSOR fortement typée ou faiblement typée dans la définition de procédure ou fonction stockée sur le serveur Oracle. Un jeu de résultats de fortement typé est retourné pour les paramètres REF CURSOR fortement typée et un jeu de résultats de faiblement typée est retourné pour faiblement typée des paramètres REF CURSOR (par exemple, les paramètres déclarés avec un type SYS_REFCURSOR).  
  
 Le code suivant illustre le code XML pour un paramètre de sortie REF CURSOR fortement typée.  
  
```  
<[PARAM_NAME]>  
 <[PARAM_NAME]RECORD>  
  <[COL1_NAME]>value1</[COL1_NAME]>  
  <[COL2_NAME]>value2</[COL2_NAME]>  
  ...  
 </[PARAM_NAME]RECORD>  
</[PARAM_NAME]>  
  
[PARAM_NAME] = OUT REF CURSOR parameter name; for example, EMP_REFCURSOR  
[COL_NAME] = Name of a column in the REF CURSOR type; for example, Name.  
```  
  
 Le code suivant illustre le code XML pour un paramètre de sortie REF CURSOR faiblement typée.  
  
```  
<[PARAM_NAME]>  
 <GenRecordRow xmlns="oracledb">  
  <GenRecordColumn>  
   <ColumnName>COL_NAME</ColumnName>  
   <ColumnValue>COL_VALUE</ColumnValue>  
   <ColumnType>COL_TYPE</ColumnType>  
  </GenRecordColumn>  
  …  
 </GenRecordRow>  
 …  
</[PARAM_NAME]>  
  
[COL_NAME] = Name of column; for example, Name  
[COL_VALUE] = Column value; for example, Scott  
[COL_TYPE] = Column data type; for example, System.String  
```  
  
## <a name="in-out-ref-cursor-parameters"></a>DANS les paramètres REF CURSOR  
 Étant donné que le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] modélise les paramètres IN REF CURSOR comme des chaînes et des paramètres de sortie REF CURSOR en tant que types complexes, il ne peut pas prendre en charge un seul type d’un paramètre dans des REF CURSOR. Pour cette raison, il traite des paramètres dans des REF CURSOR comme deux paramètres différents : un paramètre IN dans le message de demande et d’un paramètre OUT dans le message de réponse.  
  
 Pour éviter un conflit de nom dans la programmation du modèle de service, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ajoute la chaîne « _IN » pour le paramètre IN dans le message de demande pour un paramètre donné nommé [PARAM_NAME], deux paramètres sont ainsi créés :  
  
-   [PARAM_NAME] _IN est un paramètre IN REF CURSOR dans la procédure stockée ou d’un message de demande de fonction. Il contient une instruction de PL/SQL (une requête select ou un appel de fonction ou procédure stocké) qui retourne les REF CURSOR.  
  
-   [PARAM_NAME] est un paramètre de sortie REF CURSOR dans la procédure stockée ou d’un message de réponse de fonction. Il contient des REF CURSOR en tant qu’un jeu de résultats fortement typée ou faiblement typée.  
  
> [!IMPORTANT]
>  L’adaptateur ne peut pas prendre en charge une procédure ou fonction qui contient un paramètre IN nommé [PARAM_NAME] _IN et un paramètre dans les REF CURSOR nommé [PARAM_NAME]. Il s’agit, car l’adaptateur attend un paramètre nommé _IN [PARAM_NAME] pour représenter l’entrée pour le paramètre REF CURSOR et vous ne pouvez pas spécifier les deux paramètres dans le message de demande.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)