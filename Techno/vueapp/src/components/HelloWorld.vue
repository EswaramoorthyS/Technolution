<template>
  <div class="alin">
    <center>
    <table border="1">
                <tr>Student Result board </tr>
                <tr style="font-style: italic;">
                    <th>Name</th>
                    <th>Roll Number</th>
                    <th>Total Marks</th>
                    <th>Status</th>
                </tr>

                   <tr v-for="(std,index) in students" :key="index">
                    <td v-bind:class="[std.status,std.grade]" style="text-transform: capitalize;">{{std.name}}</td>
                    <td v-bind:class="[std.status,std.grade]"> {{std.rollNumber}}</td>
                    <td v-bind:class="[std.status,std.grade]"> {{std.total}}</td>
                   <td v-bind:class="[std.status,std.grade]">{{std.status}}</td>
                </tr>
            </table>
    </center>
  </div>
</template>

<script>

  var students = [{
            name: 'rajiv',
            marks: {
                Maths: 18,
                English: 21,
                Science: 45
            },
            rollNumber: "KV2017-5A2 "
        }, {
            name: "abhishek",
            marks: {
                Maths: 43,
                English: 30,
                Science: 37
            },
            rollNumber: "KV2017-5A1"
        }, {
            name: "zoya",
            marks: {
                Maths: 42,
                English: 31,
                Science: 50
            },
            rollNumber: "KV2017-5A3"
        }]



students.sort(function(x, y) {

    let a = x.name,
        b = y.name;
    return a == b ? 0 : a > b ? 1 : -1;
});
  students.forEach(updateStatus);
var a=students.reduce((max,totalArray)=>{
    return totalArray.total >=max.total ? totalArray:max;
})
var b=students.findIndex(item=> item.total===a.total);
students[b]['grade']="Topper";

function updateStatus(item, index, arr){
  arr[index]['total'] = item.marks.Maths + item.marks.English + item.marks.Science;
  arr[index]['status'] = item.marks.English >20 && item.marks.Maths > 20 && item.marks.Science >20? "Pass":"Fail";
  
}
console.log(students);
export default {
  name: 'HelloWorld',
  data(){
    return {
      students        
    }
  },
 
  }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only-->
<style scoped>
.alin{
  text-align: center;
}

.Fail
{
color:red;
}
.pass{
  color: black;
}
.Topper
{
color:green;
}
</style>
