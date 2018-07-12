# Scripts_MILA
# Este proceso desarrolla el Proceso de valoración de Acciones en MILA

setwd("S:/INFO_VALORACION/ACCIONES/AÑO 2018/MILA_MGC")
fecha=as.Date(Sys.Date())
nombre_archivo=paste0("MGC_",fecha,".csv")

MGC=read.table(nombre_archivo,header = FALSE, sep = ",", check.names = FALSE, fill=FALSE, quote="")


NEMO_MGC=as.character(MGC[,1])
fecHas_mgc=as.character(fecha,format="%Y-%m-%d")
Precio1=as.character(MGC[,3])
precio2=as.character(MGC[,4])
precio3=as.character(MGC[,5])
PAIS=as.character(MGC[,6])
MONEDA=as.character(MGC[,7])

MGC_PRECIOS=cbind(NEMO_MGC,fecHas_mgc,Precio1,precio2,precio3,PAIS,MONEDA)

##MILA
  
nombre_archivo=paste0("MILA_",fecha,".csv")

MILA=read.table(nombre_archivo,header = FALSE, sep = ",", check.names = FALSE, fill=TRUE, quote="")

NEMO_MILA=as.character(MILA[,1])
fecHas_MILA=as.character(fecha,format="%Y-%m-%d")
Precio1_MI=as.character(MILA[,3])
precio2_MI=as.character(MILA[,4])
precio3_MI=as.character(MILA[,5])
PAIS_MI=as.character(MILA[,6])
MONEDA_MI=as.character(MILA[,7])

MILA_PRECIOS=cbind(NEMO_MILA,fecHas_MILA,Precio1_MI,precio2_MI,precio3_MI,PAIS_MI,MONEDA_MI)

### Combinar Archivos

archivo_MILA_MGC=rbind(MILA_PRECIOS,MGC_PRECIOS)

write.table(archivo_MILA_MGC,paste0("S:/INFO_VALORACION/ACCIONES/AÑO 2018/Carga MILA/PMGCYMI",format(fecha, "%d%m"),".csv"),col.names=F, quote=F, sep=",", row.names = FALSE)
