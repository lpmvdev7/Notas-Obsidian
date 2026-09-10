Tipo: Nota permanente
Fecha: 2026-08-06
Referencias:
* Linux.pdf
Temas: #filesystem 


| Sistema de archivos | Descripcion breve                                                                                                            |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| ext4                | Sistema de archivos predeterminado en distros de linux modernas. Soporta archivos grandes, journaling mejorado y mas rapido. |
| XFS                 | Sistema de archivo optimizado para el manejo de archivos grandes. Ampliamente usado en servidores.                           |
| Btrfs               | Sistema de archivos diseñado para ser el futuro de linux, soporta snapshots, compresión y verificación de integridad         |
| exFAT               | Alternativa FAT32 para discos compartidos entre Windows y Linux. Soporta archivos grandes.                                   |
| NTFS                | Sistema de archivos de Windows.                                                                                              |

| Sistema de Archivos | Casos de Uso Recomendados                                                         |
| ------------------- | --------------------------------------------------------------------------------- |
| ext4                | Sistemas de escritorio, Servidores generales, Gaming, Laptops                     |
| XFS                 | Servidores con archivos grandes, Sistemas con muchas escrituras, Edicion de video |
| Btrfs               | Sistemas avanzados, Backups automaticos                                           |
| exFAT               | Discos externos compartidos entre Windows y Linux, Almacenamiento portatil.       |
| NTFS                | Particiones de Windows, Dual Boot Windows-Linux                                   |

### Notas Relacionadas
[[df]]
[[lsblk]]

