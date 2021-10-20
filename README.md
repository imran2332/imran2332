<?php

$conn = mysqli_connect('localhost','root','','stdpro');
if(isset($_POST['btn'])){
  $stdname = $_POST ['stdname'];
  $stdreg = $_POST['stdreg'];

if(!empty($stdname) && !empty($stdreg)){

  $query = "INSERT INTO stduent(stdname,stdreg)VALUE('$stdname',$stdreg)";
  $createquery = mysqli_query($conn,$query);
  if($createquery){
    echo "Your Data Submiteated";
  }


}
else{
  echo "Field should not be emptpy";
}



}
?>


<?php


if(isset($_GET['delete'])){
  $stdid = $_GET['delete'];
  $query = "DELETE FROM stduent WHERE id={$stdid}";
  $deletequery = mysqli_query($conn,$query);
  if($deletequery){
    echo "Data Deleted";
  }
}

?>


<!doctype html>
<html lang="en">
  <head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">

    <title>Crud</title>
  </head>
  <body>

  


  <div class="container shadow m-5 p-3">
    <form action="" method="POST" class="d-flex justify-content-around">
      <input  class="form-control" type="text" name="stdname" placeholder="Enter Your Name ">
      <input  class="form-control" type="number" name="stdreg" placeholder="Enter Your Reg ">
      <input type="Submit" value="send" name="btn" class="btn btn-success">
    </form>

  </div>

<div class="container">
  <table class="table table-bordered">
    <tr>
      <th>STD ID</th>
      <th>STD NAME</th>
      <th>reg</th>
      <th></th>
      <th></th>
    </tr>
    <?php
   
   $query = "SELECT * FROM stduent";
   $readquery = mysqli_query($conn,$query);
   if($readquery->num_rows >0){
     while($rd = mysqli_fetch_assoc($readquery)){
       $stdid = $rd['id'];
       $stdname = $rd['stdname'];
       $stdreg = $rd['stdreg'];
     
   
    ?>
  <tr>
      <td><?php echo $stdid; ?></td>
      <td><?php echo $stdname; ?></td>
      <td><?php echo $stdreg; ?></td>
      <td><a href="index.php?delete=<?php echo $stdid; ?>" class="btn btn-danger
      ">DELET</a></td>
      <td></td>
    </tr>
    <?php }}else{
      echo "No Data to show";
    } ?>
  </table>
</div>








    <!-- Optional JavaScript; choose one of the two! -->

    <!-- Option 1: Bootstrap Bundle with Popper -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-ka7Sk0Gln4gmtz2MlQnikT1wXgYsOg+OMhuP+IlRH9sENBO0LRn5q+8nbTov4+1p" crossorigin="anonymous"></script>

    <!-- Option 2: Separate Popper and Bootstrap JS -->
    <!--
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.10.2/dist/umd/popper.min.js" integrity="sha384-7+zCNj/IqJ95wo16oMtfsKbZ9ccEh31eOz1HGyDuCQ6wgnyJNSYdrPa03rtR1zdB" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.min.js" integrity="sha384-QJHtvGhmr9XOIpI6YVutG+2QOK9T+ZnN4kzFN1RtK3zEFEIsxhlmWl5/YESvpZ13" crossorigin="anonymous"></script>
    -->
  </body>
</html>
--->
