<template>
    <table>
        <thead>
            <tr>
                <th>사원번호</th>
                <th>이름</th>
                <th>성</th>
                <th>직무</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="emp in empList" v-bind:key="emp.employeeId">
                <td v-text="emp.employeeId"/>
                <td>{{emp.firstName}}</td>
                <td v-text="emp.lastName"/>
                <td>{{emp.jobId}}</td>
            </tr>
        </tbody>
    </table>
</template>

<script>
export default {
    name: 'EmpList',
    data: function(){
        return {
            empList: {}
        }
    },
    created: function(){
        fetch('http://localhost/empInfoList')
        .then(response => response.json())
        .then(data => {
            this.empList = data;
        })
        .catch(error => console.log(error));
    }
}
</script>
