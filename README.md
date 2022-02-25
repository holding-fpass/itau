# Itaú

Definições de integração Itaú <> FPASS

## Overview

![Overview](https://www.plantuml.com/plantuml/png/jLRDRjj64BxpAGRAnM7h7xTD3GXr6YQDMmTEODXnVHwH8sbJSfVP7rkEe8SfUkWJz90UunVh35SKPKPnsm3nGLZE_tpxxGS_SHwj3rMPUELBWi6nnzk_uOV7S7IQdPyF4WpUw52Do2RkDwLhj5Z1IvnbBbVg9Jc74peXFV5JsD_RInBClR5muSBjxrOPGCTdpar6PWQnzWFA3_RszWyU9LpCgrpLg3raTIt171Buc90kW5CaBKu23qRVVLlGGI_jaaRBpACQdOkVTmkV7g_SV5vLJcGks7xSjXn2biiw6-otVzx-OQ0WG8dWfKoSAPbO4sh8WYVD_R29Iw3Dl5FaPx9euSNbQ_PhumbA6di-f-dpUaeLUqlnmjR-dgFSwC8zJ5FsP-N4MEMdrH1-EV_cqVTiEgVSaX_2N77nPgzekGYgM3GbJ_6cD5Wq1UO9yDz0EJSOmY1D9IbD1rz7imiZCS-3Lcy3oUh7nQ9rOYWQvrXwo2QNK-Mfn16L5xPS39QLqJTHsbot9fhLZObTy1NFizefJPkGE6LcAtn76Yj6pwJf45u9VE9vRL6xYaTcWpWkpaw0nxCt4FdtvbgWaviKAEyYliQ3c7X6XRAK-nPugoRJY3nxfVhK-zeDTtS_jUVkZzplS9wcrDxKYslFcwoFm8UaeuEnwjsI3HmKpR-ILMCcIKUcFcrWVNPPfUNii9zi-hHfRhgt7sy8cNDAemyMEIdowrxsV7Z_S9dv4tgKAMbv3R2bqFUTVC_ABeVQue_MVsHiXPu7HL25BDdDliMCYs4VtcUviGNoOBMbAzNmW81_B4Mfs6vUsGv7hr-s73jOdrdY3ddCxb0KsEv2-3Iul1awjDh4NMccd6_Q2h50REQA2cCxEFdRhih4_T8ZLNfhd5GRITab_6cJpXlR7M4r71x2V9qpEmpbeXz9CqzMOtbSV1pFM2twsmi0fIDuXivqksZ1bd4mZ9uWkWslp5NdJpw12iEdLenierjrwmjL8upFjLV-PbrPWeY62CKy28MMsY40Y0QSg36LHa_WXD1gigssjFjBdbZMSpu6JR9YJ0TNZEp35HMedIAtX9wAp4iR4IWshx_R-t7f7Xi_o98fx9NHyRdrmUb7mDP1WJV_GSF7_rU_cuGD0lw5f5lM-1VPVchDDNVVgDndz3OefnZAlyY97Z2wz-FVQZUdUcCrRaH_yoDmz0RN7i5dN-vdJjLAK_FJat9vEyl_C0oKPYBZFU70K9N_0000)

## Glossário

Como forma de equiparar estruturas informacionais nos respectivos sistemas, seguem as definições:

- **Ephemeral JWT**: Token gerado pelo Itaú utilizando chave secreta comum (Itaú e FPASS) que tem duração de 10 segundos
- **Application JWT**: Token gerado pelo FPASS utilizando chave secreta própria do FPASS

## Autenticação

Identidade do usuário será realizada por JWT (Ephemeral JWT), emitida pelo Itaú e verificada pelo FPASS. O envio será por _query param_ junto a URL.
Chave de verificação (Verify Signature Secret - https://jwt.io) será definida em conjunto pelo Itaú e FPASS.

## Autorização

A autenticidade do JWT (Ephemeral JWT) será verificada utilizando chave secreta comum (Itaú e FPASS) sobre os critérios demostrados no fluxo (vide imagem). Uma vez verificada será gerado um JWT da aplicação FPASS (Application JWT).

## Ephemeral JWT

- **iss**: Enumeração do emissor: Ex.: itau
- **sub**: Identificação do usuário, sendo esse id informação que dê unicidade a este usuário. Ex.: V1StGXR8_Z5jdHi6B-myT
- **aud**: Escopo de acesso a ser concedido. Ex.: edu.itau.com.br
- **iat**: Momento da emissão. Ex.: 1516239022
- **exp**: Tempo de expiração do token emitido. Ex.: 1516239032

## Application JWT

- **iss**: Enumeração do emissor: Ex.: fpass
- **sub**: Identificação do usuário Ex.: d5353f17-918c-454d-a76f-c05b552eb761
- **aud**: Escopo de acesso a ser concedido. Ex.: edu.itau.com.br
- **iat**: Momento da emissão. Ex.: 1516239022
- **exp**: Tempo de expiração do token emitido. Ex.: 1517239032
