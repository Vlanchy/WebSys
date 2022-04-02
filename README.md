<?php
    // var_dump($_SERVER["REQUEST_METHOD"]);

    $fName = $_POST['fName'] ?? null; 
    $lName = $_POST['lName'] ?? null;
    $bday = $_POST['bday'] ?? null;
    $gender = $_POST['bday'] ?? null;
    $address = $_POST['address'] ?? null;
    $username = $_POST['username'] ?? null;
    $inputPassword = $_POST['inputPassword'] ?? null;
    $formFile = $_POST['formFile'] ?? null;
    $shortBio = $_POST['shortBio'] ?? null;
    $agree = $_POST['agree'] ?? null;
    $has_error = 0;
    $error_msg = '';
    // here
    if($_SERVER["REQUEST_METHOD"] == "POST"){
        // var_dump($_POST);
        if(!isset($fName) || strlen(trim($fName))==0){
            $has_error = 1;
            $error_msg .= '&bull; First name is required <br>';
        } if(!isset($lName) || strlen(trim($lName))==0){
            $has_error = 1;
            $error_msg .= '&bull; Last name is required <br>';
        } if(!isset($username) || strlen(trim($username))==0){
            $has_error = 1;
            $error_msg .= '&bull; Username is required <br>';
        } if(!isset($inputPassword) || strlen(trim($inputPassword))==0){
            $has_error = 1;
            $error_msg .= '&bull; Password is required <br>';
        }
        if(!isset($agree) || strlen(trim($agree))==0){
            $has_error = 1;
            $error_msg .= '&bull; Review terms and condition <br>';
        }
    }
?>
    




<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Registration</title>
    <link rel="stylesheet" href="bootstrap.css">
    <link rel="stylesheet" href="design.css">
    <script src="bootstrap.bundle.js"></script>
<style>
*{
    margin: 0;
    padding: 0;
}
body{
    display: flex;
    height:auto;
    padding: 10px;
    background: linear-gradient(135deg, #71b7e6, #9b59b6);
}
.container-sm{
    max-width: 700px;
    max-height: 100%;
    width: 100%;
    background: #fff;
    padding: 25px 30px;
    border-radius: 10px;
}
</style>   

</head>
<body>
    <style> type="text/css" .has_error{color: #f5c2c7} .has_error input {background-color: #f5c2c7} </style>
    
    <div class="container-sm">
        <div class="py-5 text-center">
            <h1>Registration Form</h1>
            <em class="">Fields having * are required.</em>
        </div> 
        
        <!-- alerts -->
        <?php if($has_error == 1): ?>
            <div class="col-12">
                <div class="alert alert-danger" role="alert">
                    <strong class="">Attention!</strong>
                    <p><?php echo $error_msg?></p>
                </div>
            </div>
        <?php endif; ?>

        <!-- form -->
        <div class="row my-3">
            <form action="<?php $_SERVER['PHP_SELF']; ?>" method="post">
                <div class="row g-3">
                    <!-- first name -->
                    <div class="col-6"> 
                        <div class="<?php echo ( $_SERVER['REQUEST_METHOD'] === 'POST' && ( !isset($fName) || strlen(trim($fName)) == 0 ) ? 'has_error' : '' ); ?>">                        
                            <label for="fName" class="form-label">First Name *</label>
                            <input type="text" class="form-control" id="fName" name="fName" placeholder="First Name" value="<?php echo $fName;?>">
                        </div>
                    </div>
                    <!-- last name -->
                    <div class="col-6">
                        <div class="<?php echo ( $_SERVER['REQUEST_METHOD'] === 'POST' && ( !isset($lName) || strlen(trim($lName)) == 0 ) ? 'has_error' : '' ); ?>">                        
                            <label for="lName" class="form-label">Last Name *</label>
                            <input type="text" class="form-control" id="lName" name="lName" placeholder="Last Name" value="<?php echo $lName;?>">
                        </div>
                    </div>
                </div>

                <div class="row my-3">
                    <!-- birthday -->
                    <div class="col-6">
                        <label for="bday" class="form-label">Birthday</label>
                        <input type="date" class="form-text text-muted form-control" id="bday" name="bday">
                    </div>
                    <!-- gender -->
                    <div class="col-6">
                        <label for="gender" class="form-label">Gender</label>
                        <select class="form-select" id="gender" name="gender">
                            <option value="" class="form-text text-muted">Please Select</option>
                            <option >Female</option>
                            <option>Male</option>
                            <option>I prefer not to say</option>
                        </select>
                        <div class="invalid-feedback">
                              Please provide a valid gender.
                        </div>
                    </div>
                    <!-- address -->
                    <div class="col-12 my-3">
                        <label for="address" class="form-label">Address</label>
                        <input type="text" class="form-control" id="address" name="address" placeholder="Address">
                    </div>
                    <!-- username -->
                    <div class="col-12 my-1">
                        <div class="<?php echo ( $_SERVER['REQUEST_METHOD'] === 'POST' && ( !isset($username) || strlen(trim($username)) == 0 ) ? 'has_error' : '' ); ?>">                                                
                            <label for="username" class="form-label">Username *</label>
                            <input type="text" class="form-control" id="username" name="username" placeholder="Username" value="<?php echo $username;?>">
                        </div>
                    </div>
                    <!-- password -->
                    <div class="col-12 my-2">
                        <div class="<?php echo ( $_SERVER['REQUEST_METHOD'] === 'POST' && ( !isset($inputPassword) || strlen(trim($inputPassword)) == 0 ) ? 'has_error' : '' ); ?>">                                                
                            <label for="inputPassword" class="col-sm-2 col-form-label">Password *</label>
                            <input type="password" class="form-control" id="inputPassword" name="inputPassword" placeholder="Password" > 
                            <div class="pt-1">
                                <input type="checkbox" onclick="myFunction()"> Show Password
                            </div>
                            
                            <script>
                                function myFunction() {
                                    var x = document.getElementById("inputPassword");
                                    if (x.type === "password") {
                                        x.type = "text";
                                    } else {
                                        x.type = "password";
                                    }
                                }
                            </script>
                        </div>
                    </div>
                    <!-- photo -->
                    <div class="col-12 my-2">
                        <label for="formFile" class="form-label">Photo</label>
                        <input class="form-control" type="file" id="formFile" name="formFile">
                    </div>
                    <!-- short bio -->
                    <div class="col-12 my-2">
                        <label for="shortBio" class="form-label">Short Bio</label>
                        <input type="text" class="form-control"  id="shortBio" name="shortBio" placeholder="Describe Yourself">
                    </div>
                    <!-- agree_terms -->
                    <div class="col-12 mt-5">
                        <div class="form-check ">
                          <input class="form-check-input" type="checkbox" value="0" id="invalidCheck2" name="agree">
                          <label class="form-check-label" for="invalidCheck2">
                            Agree to terms and conditions
                          </label>
                        </div>
                    </div>
                    <!-- submit button -->
                    <div class="col-12 my-2">
                        <button class="btn btn-primary" type="submit">Submit form</button>
                    </div>
                </div>
            </form>
        </div>
    </div>
        
</body>
</html>