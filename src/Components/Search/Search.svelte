<script>
    import { personsList } from '../../utils/mockData';
    import  ResultsContainer  from  './ResultsContainer.svelte';
    import Input from './Input.svelte';

    let searchQuery = '';
    let minQueryLength = 3;
    let filteredPeoples = [];

    const groupBy = (array, key) => {
        return array.reduce((result, currentValue) => {
            (result[currentValue[key]] = result[currentValue[key]] || []).push(currentValue);
            return result;
        }, {});
    };

    function fetchResults (event) {
        searchQuery = event.target.value.trim().toLowerCase();
        
       if((searchQuery).length >= minQueryLength){
            filteredPeoples = personsList.filter((item) =>
                 item.first_name.toLowerCase().includes(searchQuery) ||
                 item.last_name.toLowerCase().includes(searchQuery) ||
                 item.id.toLowerCase().includes(searchQuery) ||
                 item.email_address.toLowerCase().includes(searchQuery)
           ) 
        filteredPeoples = groupBy(filteredPeoples, 'relationship');
       } 
    }

    function clearSearchQuery () {
        searchQuery = '';
    }

</script>

<Input fetchResults={(event) => fetchResults(event)} 
       clearSearchQuery={() => clearSearchQuery()} 
       searchQuery={searchQuery}/>

{#if searchQuery.length >= minQueryLength}
    <ResultsContainer results={filteredPeoples}/>
{/if}