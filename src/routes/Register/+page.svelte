<script>
    let color = "red";
</script>


<main>

<div class="flex-container">
    <div style="width: 100px; height: 100px; border-radius: 50%; overflow:hidden; background-color:{color};"></div>
  <h1>Register</h1>
  <form>
    <label>Login <br> <label></label> Username:
            <input type="text" name="login-name" required />
    </label>
    <label>Password:
            <input type="password" name="login-password" required />
    </label>

    <label>färg:

        <select name="färg" bind:value={color}>
            <option value="red">Röd</option>
            <option value="blue">Blå</option>
            <option value="green">Grön</option>
            <option value="yellow">Gul</option>
        </select>
    </label>
  </form>
        </div>

</main>

<style>
 main{
        background-image: url("https://t4.ftcdn.net/jpg/05/21/65/59/360_F_521655929_N80d5GaCQJ2VP073PfTXJTe9mkvsNtHE.jpg");
        background-size: cover;
        width: 100%;
        height: 100%;
        padding: 5%;
    }
    form{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: end;
        gap: 20px;
    }
    
    
    .flex-container{
        border: solid 5px rosybrown;
        border-radius: 10px;
        width: 35%;
        height: 80%;
        background-color: #3a2e3b;
        margin: auto;
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        align-items: center;
}   
</style>
