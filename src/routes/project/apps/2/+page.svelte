<script>
    let expenses = [];

    let newName ='';
    let newAmount = '';

    function addExpense(){
        if (newAmount !== '') {
            const obj ={
                name : newName,
                amount: parseInt(newAmount),
            };
            expenses.push(obj);
            expenses = expenses;
            newName ='';
            newAmount = '';
        }
    }

    function deleteExpense(index){
        expenses.splice(index, 1)
        expenses = expenses
    }
</script>
<main>
    <h1>Учет расходов</h1>
    <form on:submit|preventDefault={addExpense}>
        <input bind:value={newName}/>
        <input bind:value={newAmount} />
        <button on:click={addExpense}><span>Добавить</span></button>
    </form>
    <table>
        <thead>
            <tr>
                <th>Название</th>
                <th>Сумма</th>
                <th>Деньги</th>
            </tr>
        </thead>
        <tbody>
            {#each expenses as expenses, i}
                <tr>
                    <td><div>{expenses.name}</div></td>
                    <td><div>{expenses.amount}</div></td>
                    <td><button on:click={()=> deleteExpense(i)}>Удалить</button></td>
                </tr>
            {/each}
        </tbody>
    </table>
       
</main>
<style>
    h1{
        font-size: 24px;
        margin-bottom: 20px;
    }
    button{
        padding: 5px 10px;
        background-color: #006d04;
        color: white;
        border: none;
        border-radius: 5px;
        cursor: pointer;
    }
    th{
        background-color: #eee;
    }
    th, td{
        border: 1px solid #ccc;
        padding: 8px;
        text-align: left;
    }

    table{
        margin-top: 20px;
        border-collapse: collapse;
        width:100%;
    }
</style>