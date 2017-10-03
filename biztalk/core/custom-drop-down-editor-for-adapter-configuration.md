---
title: "Éditeur de liste déroulante personnalisé pour la Configuration de l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a1b0961-652f-42b8-a18a-17abe9542cdd
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b88e5eb887c2177783611ada8e3ce2a80a0b6a66
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="custom-drop-down-editor-for-adapter-configuration"></a>Éditeur de liste déroulante personnalisé pour la Configuration de l’adaptateur
Le code de l’éditeur personnalisé montre un éditeur dérivé de la **System.Drawing.Design.UITypeEditor** classe qui affiche une zone de texte de la liste déroulante pour entrer un mot de passe. Le **GetEditStyle** supplante **UIEditorEditStyle.DropDown** pour indiquer un sous-contrôle de liste déroulante. Les méthodes de service **DropDownControl** et **CloseDropDown** gèrent le contrôle créé avec **CreatePassword**.  
  
 Le code suivant correspond à la définition de classe pour l'éditeur déroulant personnalisé :  
  
```  
/*************************************************************************  
 * Copyright (c) 1999-2004 Microsoft Corporation. All rights reserved.   *  
 *                                                                       *  
 * THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF ANY *  
 * KIND, WHETHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE  *  
 * IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A PARTICULAR *  
 * PURPOSE. THE ENTIRE RISK OF USE OR RESULTS IN CONNECTION WITH THE USE *  
 * OF THIS CODE AND INFORMATION REMAINS WITH THE USER.                   *  
 *************************************************************************/  
  
using System;  
using System.ComponentModel;  
using System.Drawing.Design;  
using System.Windows.Forms;  
using System.Windows.Forms.Design;  
using System.Security;  
using System.Security.Permissions;  
using Microsoft.BizTalk.Adapter.Framework;  
using Microsoft.BizTalk.Adapter.Framework.Forms;  
  
namespace AdapterManagement.ComponentModel {  
   /// <summary>  
   /// PasswordUITypeEditor implements a user interface for acquiring passwords  
   /// within a visual designer.  
   /// </summary>  
   public class PasswordUITypeEditor : UITypeEditor {  
      public const char PasswordChar = '\u25cf';  
      private IWindowsFormsEditorService _service = null;  
      private TextBox _password = null;  
  
      [SecurityPermissionAttribute(SecurityAction.LinkDemand)]  
      public override UITypeEditorEditStyle GetEditStyle(ITypeDescriptorContext context) {  
         if (null != context && null != context.Instance) {  
            return UITypeEditorEditStyle.DropDown;  
         }  
         return base.GetEditStyle(context);  
      }  
  
      [SecurityPermissionAttribute(SecurityAction.LinkDemand)]  
      public override object EditValue(ITypeDescriptorContext context,   
                               IServiceProvider provider,  
                               object value) {  
         if (null != context && null != context.Instance && null != provider) {  
            this._service = (IWindowsFormsEditorService) provider.GetService   
                        (typeof(IWindowsFormsEditorService));  
            if (null != this._service) {  
               this._password = CreatePassword();  
               this._service.DropDownControl(this._password);  
               value = this._password.Text;  
            }  
         }  
         return value;  
      }  
  
      private TextBox CreatePassword () {  
         TextBox password = new TextBox();  
         password.PasswordChar = PasswordUITypeEditor.PasswordChar;  
         password.Leave += new EventHandler(password_Leave);  
      }  
  
      private void password_Leave(object sender, EventArgs e) {  
         if (null != this._service) {  
            this._service.CloseDropDown();  
         }  
      }  
   } // PasswordUITypeEditor  
} // Microsoft.BizTalk.Adapter.Framework.ComponentModel  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteur de Configuration d’adaptateur personnalisé](../core/custom-adapter-configuration-designer.md)   
 [Éditeur de boîte de dialogue modales personnalisé pour la Configuration de l’adaptateur](../core/custom-modal-dialog-editor-for-adapter-configuration.md)   
 [Convertisseur de Type personnalisé pour la Configuration de l’adaptateur](../core/custom-type-converter-for-adapter-configuration.md)   
 [Composants de Configuration avancée pour les cartes](../core/advanced-configuration-components-for-adapters.md)