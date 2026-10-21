# MF Construcciones · Armador de presupuestos

Web app de un solo archivo (`index.html`, sin instalación) para armar presupuestos de obra, descargarlos en PDF y enviarlos por WhatsApp.

## Qué hace
- **Datos de la empresa** (nombre, propietario, teléfono, email, CUIT, dirección): se cargan una vez y quedan guardados en el navegador. Salen en el PDF y en el mensaje.
- **Mano de obra:** concepto + medida + unidad + precio por unidad; el subtotal se calcula solo.
  Se pueden elegir trabajos predefinidos por rubro (Revoques, Albañilería, Techos, etc.) o escribir uno a mano.
- **Materiales:** se elige si quedan **a cargo del cliente** (no suman) o si se **incluyen** en el presupuesto, cargándolos con cantidad × precio por unidad (hay materiales predefinidos). El total suma mano de obra + materiales y el PDF muestra cada subtotal.
- **Cálculo en vivo:** panel flotante a la derecha (y barra fija abajo en el celular) con el detalle y el total.
- **Condiciones** con texto predeterminado, editable (forma de pago, plazo, observaciones, validez).
- **PDF** prolijo con espacio para firma / conformidad del cliente.
- **WhatsApp:** se escribe el número del cliente y se abre el chat con el mensaje armado (editable, con variables como `{cliente}`, `{total}`, `{plazo}`). El PDF se descarga y se adjunta en el chat.
- El borrador se guarda solo; "Nuevo presupuesto" mantiene los datos de la empresa y suma 1 al número.

## Subir a GitHub
1. Crear un repositorio nuevo (ej: `mf-presupuestos`).
2. Subir `index.html`, `vercel.json`, `package.json` y `README.md` ("Add file → Upload files") o por terminal:
   ```bash
   git init && git add . && git commit -m "Presupuestos MF"
   git branch -M main
   git remote add origin https://github.com/TU_USUARIO/mf-presupuestos.git
   git push -u origin main
   ```

## Publicar en Vercel
1. Entrar a https://vercel.com con GitHub → **Add New → Project** → elegir el repo.
2. Framework Preset: **Other** (sin build command ni output directory) → **Deploy**.

## Notas
- Número del cliente: código de área sin 0 ni 15 (ej: `3537123456`). Se agrega el prefijo `549`.
- Los datos se guardan en el navegador de cada dispositivo (no se sincronizan entre celular y PC).
- Necesita internet para cargar la librería de PDF (jsPDF).
