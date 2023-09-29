<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Age Calculator</title>
    <style>
        * {
            background-color: rgb(61, 59, 59);
            color: white;
            font-style: normal;
            font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
        }

        #header {
            text-decoration: underline;
            font-size: 40px;
            position: relative;
            top: 100px;
        }

        .label {
            font-size: 20px;
            position: relative;
            top: 130px;
        }

        .inputField {
            position: relative;
            left: 30px;
            top: 130px;
            border-radius: 7px;
            border: 2px white solid;
            height: 38px;
            width: 282px;
            font-size: 18px;
        }

        #submit {
            padding: 10px, 20px;
            font-size: 18px;
            border: 2px white solid;
            height: 35px;
            width: 100px;
            border-radius: 10px;
            position: relative;
            top: 157px;
            left: 40px;
        }

        #reset {
            padding: 10px, 20px;
            font-size: 18px;
            border: 2px white solid;
            height: 35px;
            width: 100px;
            border-radius: 10px;
            position: relative;
            top: 157px;
            left: 80px;
        }

        #ansField {
            position: relative;
            top: 180px;
        }

        #age {
            position: relative;
            top: 180px;
            right: 10px;
            left: 40px;
            padding: 8px 0px 0px 0px;
            width: 283px;
            height: 35px;
            /* right: 20px; */
        }
    </style>
</head>

<body>

    <center>
        <h1 id="header">Age Calculator</h1>
        <table>
            <tr>
                <td>
                    <label for="year" class="label">Enter YOB</label>
                    <!-- <input type="text" id="year" class="inputField" placeholder="YYYY">  only for year -->
                    <input type="date" id="year" class="inputField" placeholder="YYYY" required>

                </td>
            </tr>
        </table>

        <button type="button" id="submit">Submit</button>
        <button type="button" id="reset">Re-set</button>

        <div id="ansOutput">
            <table>
                <tr>
                    <td><label for="age" class="label" id="ansField">Your age</label></td>
                    <td>
                        <div type="text" class="inputField" id="age"></div>
                    </td>
                </tr>
            </table>
        </div>
    </center>


    <script>




        var submit = document.querySelector("#submit")
        var age = document.querySelector("#age")
        var reset = document.querySelector("#reset")
        submit.addEventListener("click", function () {
            var year = document.querySelector("#year").value
            var finalform = year.split("-")

            let inputDate1 = finalform[2]
            let inputMonth = finalform[1]
            let inputYear = finalform[0]

            var obj = new Date()
            var finalYear;
            var finalDate;
            var finalMonth;

            var presentMonth = obj.getMonth()+1
            var presentDate = obj.getDate()
            var presentYear = obj.getFullYear()
            var monthdays = [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]
            // Year Gap Calculation
            if (presentMonth > inputMonth || (presentMonth == inputMonth && presentDate >= inputDate1)) {
                finalYear = presentYear - inputYear
            }
            else {
                finalYear = presentYear - inputYear - 1
            }

            // Months Calculation
            if (presentMonth > inputMonth) {
                finalMonth = presentMonth - inputMonth;
            }
            else if (presentMonth == inputMonth) {
                finalMonth = 12 + presentMonth - inputMonth - 1 ;
            }
            else {

                finalMonth = 12 + presentMonth - inputMonth
            }
            // days calculation
            var monthdays = [0, 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]
            if (presentDate >= inputDate1) {
                finalDate = presentDate - inputDate1
            }
            else {
                let Month=inputMonth.split("")
                let firstDig=Number(Month[0]);
                let secondDig=Number(Month[1]);
                if(firstDig==0)
                {
                    finalDate = presentDate - inputDate1 + monthdays[secondDig]
                }
                else{
                    finalDate = presentDate - inputDate1 + monthdays[inputMonth]
                }
            }

            age.innerHTML = `${finalYear} years ${finalMonth} months ${finalDate} days`
        })

        reset.addEventListener("click", function () {
            document.querySelector("#year").value = "none"
            age.innerHTML = ""
        })



    </script>
</body>

</html>
