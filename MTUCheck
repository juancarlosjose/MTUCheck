# Author ; Juan Carlos José Montero Prieto - Programador Diseñador de Software
# Licenia Libre
# Programa de Chequeo de MTU (Maximum Transmission Unit) es una medida que representa el tamaño máximo de los paquetes de datos que un dispositivo conectado a una red aceptará. 
# gatewayIP será la direccion de tu DNS de confianza y al que estás apuntando este ejemplo es a GoogleDNS Primary

$gatewayIP = "8.8.8.8"  Aqui ingresa el IP de tu DNS Primario para obtener el Óptimo MTU

# Inicializa el valor máximo de MTU donde maxMTU será el valor maximo de arranque de pruebas donde el valor máximo puede ir de 1500 para las redes Normales pero en algunos casos puede llegar a 9000 en jumbo frames en fibra óptica.

$maxMTU = 1500
$minMTU  = 1200
# Ejecuta un bucle para probar diferentes tamaños de MTU desde el maximo maxMTU al Minimo MinMTU
while ($maxMTU -ge $minMTU) {
    $result = Test-Connection -ComputerName $gatewayIP -Count 1 -BufferSize $maxMTU -Quiet

    if ($result) {
        Write-Host "MTU de $maxMTU funciona correctamente."
        break
    }
    else {
        Write-Host "MTU de $maxMTU no funciona. Probando con un valor menor..."
        $maxMTU--
    }
}
Clear
Write-Host "El mejor MTU para tu conexión de intranet es: $maxMTU"
netsh interface ipv6 set subinterface "Wi-Fi" mtu=$maxMTU store=persistent
netsh interface ipv4 set subinterface "Wi-Fi" mtu=$maxMTU store=persistent
Write-Host "Asignacion de nuevo MTU Lista"
netsh interface ipv4 show subinterfaces


