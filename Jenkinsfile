import java.text.SimpleDateFormat

pipeline
{
    agent any
    
    environment
    {
        RUTA_FICHERO = "C:\\PRUEBA_JENKINS.txt"
        POBLACION_TOTAL = 220020
    }
    
    options
    {
        timeout(time:5,unit:"MINUTES")
    }
    
    stages
    {
        stage("Stage 1")
        {
            steps
            {
                script
                {
                    poblacion_neta = POBLACION_TOTAL.toInteger() * 0.8
                    println("Poblacion_neta Calculada. ${poblacion_neta}")
                }
            }
        }
        stage("Stage 2")
        {
            steps
            {
                script
                {
                    fecha = new Date()
                    formato = new SimpleDateFormat("ddMMyyyy")
                    formateado = formato.format(fecha)
                    writeFile(file: "${RUTA_FICHERO}", text:poblacion_neta.toString())
                    println("El fichero fue escrito.")
                }
            }
        }
        stage("Stage 3")
        {
            when 
            {
                expression
                {
                    dia = new Date().getDay()
                    mapa = [1:"L",2:"M",3:"Mi",4:"J",5:"V",6:"S",7:"D"]
                    return mapa[dia] == "Mi"
                }
            }
            steps
            {
                script
                {
                    println ("SOLO LOS MIERCOLES: El build actual es: ${env.BUILD_NUMBER}")
                }
            }
        }
    }
    post
    {
        always
        {
            echo "Siempre se ejecuta."
        }
        
        success
        {
            echo "Ejecucion con exito"
        }
        
        failure
        {
            echo "Ejecucion fallida"
        }
    }
}

