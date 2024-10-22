# Cosas-Solventadas-BTW


## Problema 1*: 
termius-app 
[3072:1022/203647.801802:ERROR:gl_surface_presentation_helper.cc(260)] GetVSyncParametersIfAvailable() failed for 1 times!

### Solucion 1*:
1. Instalar amdgpu-install: https://amdgpu-install.readthedocs.io/en/latest/
3. Deshabilitar WebGL en todos los buscadoes brave://gpu/
*   WebGL: Software only, hardware acceleration unavailable
*   WebGL2: Software only, hardware acceleration unavailable
*   WebGPU: Disabled
4. Reiniciar Ordenador
5. desde terminal funciona: termius-app -disable-gpu --disable-webgl-hardware-acceleration
6. /usr/share/applications/termius-app.desktop modificar linea a Exec=/opt/Termius/termius-app -disable-gpu --disable-webgl-hardware-acceleration --window --maximize %U

---------------------------
## Warining 2* journalctl -f  = log real time:
journalctl -f  Muestra alertas recurrentes: [system] Failed to activate service 'org.bluez': timed out 
### Solucion 2*:
sudo systemctl stop bluetooth.service (al ser pc de sobremesa sin bluetooth)

---------------------------
## Tip 3*: 
Si escribo "cleaR" o cualquier caracter en un comando en mayuscula sin querer, aparece "Command Not found"
### Solucion 3*:
Agrear al final del archivo "~/.bashrc": 
command_not_found_handle() {
    command="$(echo "$1" | tr '[:upper:]' '[:lower:]')"
    if command -v "$command" >/dev/null 2>&1; then
        "$command" "${@:2}"
    else
        echo "Comando no encontrado: $1"
    fi
}
---------------------------
