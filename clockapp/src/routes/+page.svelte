<svelte:head>
	<title>Clock Online</title>
	<meta charset="utf-8" />
	<meta name="viewport" content="width=device-width initial-scale=1.0, maximum-scale=1.0"/>
	<link href="https://fonts.googleapis.com/css2?family=DM+Sans:ital,opsz,wght@0,9..40,100..1000;1,9..40,100..1000&display=swap" rel="stylesheet">
</svelte:head>

<script lang='ts'>

    let hours = '' ;
    let minutes = '';
    let seconds = '';
    let type = '';
    let date = ''

	function startClock() {

        console.log('Page loaded')
        
        function updateClock() {
            var now = new Date();;
            hours = now.getHours().toString();
            minutes = now.getMinutes().toString();
            seconds = now.getSeconds().toString();
            date = now.getFullYear().toString() + '/' + now.getMonth().toString() + '/' + now.getDay().toString();
            type = 'AM';

            if (Number(hours) >= 12) {
                hours = (Number(hours)-11).toString();
                type='PM';
            }


            hours = hours.padStart(2, '0');
            minutes = minutes.padStart(2, '0');
            seconds = seconds.padStart(2, '0');
        }

        updateClock();
        setInterval(updateClock, 1000);
    }

    startClock();

</script>

<div id='clock-wrapper'>
    <p id='clock-text'>
        {hours}:{minutes}:{seconds} {type}
    </p>
    <p id='date-text'>
        {date}
    </p>
</div>

<style>
    #clock-wrapper{
        display:flex;
        width:100vw;
        height:100vh;
        align-items: center;
        justify-content: center;
    }

    #date-text{
        font-size:60px;
        color:white;
        font-family: 'DM Sans';
    }

    #clock-text{
        font-size:100px;
        color:white;
        font-family: 'DM Sans';
        
    }

</style>