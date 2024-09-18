import java.text.SimpleDateFormat 

pipeline
{
    agent any
    
    environment
    {
        RUTA_FICHERO = "C:\\PRUEBA_JENKINS.txt"
        YEAR_EDAD = "01/08/1995"
    }
    
    stages
    {
        stage("Stage 1")
        {
            steps
            {
                script
                {
                    year_actual = new Date().getYear().toInteger()
                    println("Año actual:" + year_actual)
                    def date = new SimpleDateFormat("dd/MM/yyyy").parse(YEAR_EDAD)
                    println("Año Edad: " + date)
                    edad = year_actual - date.getYear().toInteger()
                    println("Año Edad: " + date.getYear().toInteger())
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
