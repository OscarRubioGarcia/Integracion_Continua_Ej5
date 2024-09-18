import java.text.SimpleDateFormat 

pipeline
{
    agent any
    
    environment
    {
        RUTA_FICHERO = "C:\\PRUEBA_JENKINS.txt"
        YEAR_EDAD = "1995"
        YEAR_ACTUAL = new Date().getYear()
    }
    
    stages
    {
        stage("Stage 1")
        {
            steps
            {
                script
                {
                    edad = YEAR_ACTUAL.toInteger() - YEAR_EDAD.toInteger()
                    println("Edad: ${edad}")
                }
            }
        }
        stage("Stage 2")
        {
            steps
            {
                script
                {
                    writeFile(file: "${RUTA_FICHERO}", text:edad.toString())
                    println("El fichero fue escrito.")
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

