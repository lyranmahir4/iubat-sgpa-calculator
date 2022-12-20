<template>
    <div
        class="block p-3 bg-white border border-gray-200 rounded-lg shadow-md hover:bg-gray-100 items-center justify-center w-96 mx-auto ">
        <div class=" justify-center align-center ">
            <h1 class="text-center p-2 text-4xl font-bold leading-none text-gray-900 md:text-4xl lg:text-4xl">IUBAT SGPA Calculator</h1>
            <table class="table-auto text-left">
                <thead class="uppercase ">
                    <tr>
                        <th scope="col" class="py-3 px-3 text-center">Subject</th>
                        <th scope="col" class="py-3 px-3 text-center">Grade</th>
                        <th scope="col" class="py-3 px-3 text-center">Credit</th>
                    </tr>
                </thead>
                <tbody>
                    <tr class="bg-white p-2 "
                        v-for="(row, index) in rows" :key="index">
                        <td>
                            <input
                                class="p-2 bg-gray-50 border border-gray-300 focus:ring-blue-500 focus:border-blue-500 block w-auto"
                                v-model="row.subject" type="text" placeholder="Example: Subject 1" />
                        </td>
                        <td>
                            <select
                                class="bg-gray-50 border border-gray-300 focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5"
                                v-model="row.grade">
                                <option value="4.0">A</option>
                                <option value="3.7">B+</option>
                                <option value="3.4">B</option>
                                <option value="3.1">B-</option>
                                <option value="2.8">C+</option>
                                <option value="2.5">C</option>
                                <option value="2.2">C-</option>
                                <option value="1.5">D+</option>
                                <option value="1.0">D</option>
                                <option value="0.0">F</option>
                            </select>
                        </td>
                        <td>
                            <input
                                class="bg-gray-50 border border-gray-300 focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5"
                                v-model="row.credit" type="number" min="1" max="50" />
                        </td>
                    </tr>
                </tbody>
            </table>

        </div>
        <div class="flex justify-center align-center p-4">
            <button
                class="text-green-700 hover:text-white border border-green-700 hover:bg-green-800 focus:ring-4 focus:outline-none focus:ring-green-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center mr-2 mb-2"
                @click="addRow">Add Row</button>
        </div>
        <div class="p-4">
            <p class="text-center font-bold	">SGPA <span class="text-green-600 hover:text-green-700 text-2xl">{{ sgpa
            }}</span></p>
        </div>
        <p class="text-sm text-center">Developed by Mahir Morshed</p>
        <p class="text-sm text-center">GitHub: <a class="font-medium text-blue-600 dark:text-blue-500 hover:underline" href="https://github.com/lyranmahir4/iubat-sgpa-calculator">iubat-sgpa-calculator</a></p>

    </div>
</template>
  
<script>
export default {
    data() {
        return {
            rows: [
                { subject: "", grade: "", credit: "" },
            ]
        }
    },
    computed: {
        sgpa() {
            let totalPoints = 0;
            let totalCredits = 0;
            this.rows.forEach(row => {
                totalPoints += row.grade * row.credit;
                totalCredits += row.credit;
            });
            return (totalPoints / totalCredits).toFixed(2);
        }
    },
    methods: {
        addRow() {
            this.rows.push({ subject: "", grade: "", credit: "" });
        }
    }
}
</script>
  